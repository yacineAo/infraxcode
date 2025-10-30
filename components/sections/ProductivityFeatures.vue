<template>
    <div id="features" class="flex flex-col w-full items-start gap-4 md:gap-8 pt-8 md:pt-12 pb-16 md:pb-[100px] px-4 sm:px-8 md:px-16 lg:px-[200px] relative overflow-hidden translate-y-[-1rem] animate-fade-in"
        :style="{ '--animation-delay': animationDelay }">
        <div class="flex flex-col w-full items-center gap-2 md:gap-4 relative">
            <h2
                class="relative w-fit font-semibold text-white text-3xl sm:text-4xl lg:text-[40px] font-display">
                {{ title }}
            </h2>
            <p class="relative max-w-[510px] font-medium text-[#ffffffb2] text-sm sm:text-base text-center">
                {{ subtitle }}
            </p>
        </div>
        <div class="flex flex-col lg:flex-row w-full relative mt-16 md:mt-[150px]">
            <div
                class="flex flex-col w-full lg:w-1/2 h-[80vh] overflow-y-auto pr-0 lg:pr-4 order-2 lg:order-1 scrollbar-hide snap-y snap-mandatory">
                <div v-for="(feature, index) in features" :key="index" :ref="el => textRefs[index] = el"
                    :data-index="index"
                    class="flex flex-col items-start gap-4 md:gap-[19.21px] min-h-[80vh] snap-start scroll-mt-16 p-4 md:p-8 lg:p-0 relative"
                    style="scroll-snap-align: start;">
                    <h3
                        class="relative w-fit bg-gradient-to-r from-[#574fa1] to-[#cca0ca] bg-clip-text text-transparent font-semibold text-2xl md:text-[32px] font-display">
                        {{ feature.title }}
                    </h3>
                    <div
                        class="relative max-w-[433px] font-normal text-[#ffffffcc] text-lg md:text-xl leading-5 w-full">
                        <span v-if="feature.subtitle" class="font-bold leading-6 block">
                            {{ feature.subtitle }} <br />
                        </span>
                        <span class="font-medium leading-6 block">
                            {{ feature.description }}
                        </span>
                    </div>
                </div>
            </div>
            <div
                class="w-full h-[80vh] sticky top-0 flex items-center justify-center pl-0 lg:pl-4 order-1 lg:order-2 px-4 lg:px-0 z-10">
                <img class="w-full h-full rounded-[5px] md:rounded-[10px] object-cover"
                    :alt="`Feature ${currentIndex + 1}`" :src="features[currentIndex]?.image" />
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const props = defineProps({
    title: {
        type: String,
        default: 'Developer-Grade Productivity for Network Engineers'
    },
    subtitle: {
        type: String,
        default: 'Explore how Diverz unifies context, automation, and safety to bring developer-grade speed to NetOps'
    },
    animationDelay: {
        type: String,
        default: '400ms'
    }
})

const features = [
    {
        title: "Unified workspace",
        subtitle: "An IDE for network operations:",
        description:
            "A dev-grade workspace for terminal work, testing, and automation, all in device context.",
        image: "https://c.animaapp.com/mhc1z55wRcb3W7/img/feature-3-1.png",
    },
    {
        title: "Connection Hub",
        subtitle: "",
        description:
            "SSH, NETCONF, RESTCONF, SNMP, gRPC, APIs with support for bastions, profiles, and session logging",
        image:
            "https://c.animaapp.com/mhc1z55wRcb3W7/img/feature-1---last-plan-1-1.png",

    },
    {
        title: "In-Context AI Assistant",
        subtitle: "",
        description:
            "Reads your sessions, parses configs, and writes vendor-correct CLI and API commands. Reversible, explainable, and safe",
        image: "https://c.animaapp.com/mhc1z55wRcb3W7/img/feature-3-1.png",

    },
]

const currentIndex = ref(0)
const textRefs = ref([])

let observer = null

onMounted(() => {
    observer = new IntersectionObserver(
        (entries) => {
            entries.forEach((entry) => {
                if (entry.isIntersecting) {
                    currentIndex.value = parseInt(entry.target.dataset.index)
                }
            })
        },
        {
            threshold: 0.5,
            rootMargin: '-10% 0px -20% 0px'
        }
    )

    nextTick(() => {
        features.forEach((_, index) => {
            const el = textRefs.value[index]
            if (el) {
                observer.observe(el)
            }
        })
    })
})

onUnmounted(() => {
    if (observer) {
        observer.disconnect()
    }
})
</script>

<style scoped>
.animate-fade-in {
    animation: fadeIn 0.8s ease forwards;
}

@keyframes fadeIn {
    from {
        opacity: 0;
        transform: translateY(-1rem);
    }

    to {
        opacity: 1;
        transform: translateY(0);
    }
}

.font-display {
    font-family: 'Inter Display', sans-serif;
}

.scrollbar-hide {
    -ms-overflow-style: none;
    /* IE and Edge */
    scrollbar-width: none;
    /* Firefox */
}

.scrollbar-hide::-webkit-scrollbar {
    display: none;
    /* Chrome, Safari, and Opera */
}
</style>