<script setup>
import { ref, computed, watch, onMounted, onUnmounted } from 'vue'
import { motion, AnimatePresence } from 'motion-v'

const props = defineProps({
  texts: {
    type: Array,
    required: true
  },
  transition: {
    type: Object,
    default: () => ({ type: 'spring', damping: 25, stiffness: 300 })
  },
  initial: {
    type: Object,
    default: () => ({ y: '100%', opacity: 0 })
  },
  animate: {
    type: Object,
    default: () => ({ y: 0, opacity: 1 })
  },
  exit: {
    type: Object,
    default: () => ({ y: '-120%', opacity: 0 })
  },
  animatePresenceMode: {
    type: String,
    default: 'wait'
  },
  animatePresenceInitial: {
    type: Boolean,
    default: false
  },
  rotationInterval: {
    type: Number,
    default: 2000
  },
  staggerDuration: {
    type: Number,
    default: 0
  },
  staggerFrom: {
    type: String,
    default: 'first'
  },
  loop: {
    type: Boolean,
    default: true
  },
  auto: {
    type: Boolean,
    default: true
  },
  splitBy: {
    type: String,
    default: 'characters'
  },
  onNext: {
    type: Function,
    default: null
  },
  mainClassName: {
    type: String,
    default: ''
  },
  splitLevelClassName: {
    type: String,
    default: ''
  },
  elementLevelClassName: {
    type: String,
    default: ''
  }
})

const emit = defineEmits()

const cn = (...classes) => classes.filter(Boolean).join(' ')

const currentTextIndex = ref(0)

const splitIntoCharacters = (text) => {
  if (typeof Intl !== 'undefined' && Intl.Segmenter) {
    const segmenter = new Intl.Segmenter('en', { granularity: 'grapheme' })
    return Array.from(segmenter.segment(text), (segment) => segment.segment)
  }
  return Array.from(text)
}

const elements = computed(() => {
  const currentText = props.texts[currentTextIndex.value]
  if (props.splitBy === 'characters') {
    const words = currentText.split(' ')
    return words.map((word, i) => ({
      characters: splitIntoCharacters(word),
      needsSpace: i !== words.length - 1
    }))
  }
  if (props.splitBy === 'words') {
    return currentText.split(' ').map((word, i, arr) => ({
      characters: [word],
      needsSpace: i !== arr.length - 1
    }))
  }
  if (props.splitBy === 'lines') {
    return currentText.split('\n').map((line, i, arr) => ({
      characters: [line],
      needsSpace: i !== arr.length - 1
    }))
  }
  return currentText.split(props.splitBy).map((part, i, arr) => ({
    characters: [part],
    needsSpace: i !== arr.length - 1
  }))
})

const getStaggerDelay = (index, totalChars) => {
  const total = totalChars
  if (props.staggerFrom === 'first') return index * props.staggerDuration
  if (props.staggerFrom === 'last') return (total - 1 - index) * props.staggerDuration
  if (props.staggerFrom === 'center') {
    const center = Math.floor(total / 2)
    return Math.abs(center - index) * props.staggerDuration
  }
  if (props.staggerFrom === 'random') {
    const randomIndex = Math.floor(Math.random() * total)
    return Math.abs(randomIndex - index) * props.staggerDuration
  }
  return Math.abs(props.staggerFrom - index) * props.staggerDuration
}

const staggerDelays = computed(() => {
  const total = elements.value.reduce((sum, word) => sum + word.characters.length, 0)
  return Array.from({ length: total }, (_, i) => getStaggerDelay(i, total))
})

const handleIndexChange = (newIndex) => {
  currentTextIndex.value = newIndex
  if (props.onNext) props.onNext(newIndex)
}

const next = () => {
  const nextIndex = currentTextIndex.value === props.texts.length - 1
    ? (props.loop ? 0 : currentTextIndex.value)
    : currentTextIndex.value + 1
  if (nextIndex !== currentTextIndex.value) {
    handleIndexChange(nextIndex)
  }
}

const previous = () => {
  const prevIndex = currentTextIndex.value === 0
    ? (props.loop ? props.texts.length - 1 : currentTextIndex.value)
    : currentTextIndex.value - 1
  if (prevIndex !== currentTextIndex.value) {
    handleIndexChange(prevIndex)
  }
}

const jumpTo = (index) => {
  const validIndex = Math.max(0, Math.min(index, props.texts.length - 1))
  if (validIndex !== currentTextIndex.value) {
    handleIndexChange(validIndex)
  }
}

const reset = () => {
  if (currentTextIndex.value !== 0) {
    handleIndexChange(0)
  }
}

let intervalId = null

const startInterval = () => {
  if (intervalId) clearInterval(intervalId)
  intervalId = null

  if (!process.client || !props.auto) {
    return
  }

  intervalId = setInterval(next, props.rotationInterval)
}

watch(
  () => [props.auto, props.rotationInterval],
  startInterval
)

onMounted(() => {
  startInterval()
})

onUnmounted(() => {
  if (intervalId) clearInterval(intervalId)
})

defineExpose({
  next,
  previous,
  jumpTo,
  reset
})
</script>

<template>
  <motion.span
    :class="cn('flex flex-wrap whitespace-pre-wrap relative', mainClassName)"
    v-bind="$attrs"
    layout
    :transition="transition"
  >
    <span class="sr-only">{{ texts[currentTextIndex] }}</span>
    <AnimatePresence :mode="animatePresenceMode" :initial="animatePresenceInitial">
      <motion.span
        :key="currentTextIndex"
        :class="cn(splitBy === 'lines' ? 'flex flex-col w-full' : 'flex flex-wrap whitespace-pre-wrap relative')"
        layout
        aria-hidden="true"
      >
        <template
          v-for="(wordObj, wordIndex) in elements"
          :key="wordIndex"
        >
          <span :class="cn('inline-flex', splitLevelClassName)">
            <template
              v-for="(char, charIndex) in wordObj.characters"
              :key="charIndex"
            >
              <motion.span
                :initial="initial"
                :animate="animate"
                :exit="exit"
                :transition="{
                  ...transition,
                  delay: staggerDelays[
                    elements
                      .slice(0, wordIndex)
                      .reduce((sum, word) => sum + word.characters.length, 0) + charIndex
                  ]
                }"
                :class="cn('inline-block', elementLevelClassName)"
              >
                {{ char }}
              </motion.span>
            </template>
            <span v-if="wordObj.needsSpace" class="whitespace-pre"> </span>
          </span>
        </template>
      </motion.span>
    </AnimatePresence>
  </motion.span>
</template>