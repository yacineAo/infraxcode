<template>
    <section class="w-full flex flex-col items-center gap-[99px] bg-black py-[137px]">
        <div class="inline-flex w-full flex-col items-center gap-8 px-4 translate-y-[-1rem] animate-fade-in">
            <!-- Title -->
            <div class="flex flex-col items-center gap-7 w-full">
                <h1 class="w-fit font-semibold text-white md:text-[56px] text-4xl text-center leading-[normal]"
                    style="font-family: 'Inter Display', Helvetica;">
                    An AI-native CLI Workspace
                </h1>

                <div
                    class="inline-flex items-center gap-2 flex-wrap justify-center translate-y-[-1rem] animate-fade-in [--animation-delay:200ms]">
                    <p class="w-fit font-medium text-[#ffffffb2] text-2xl text-center leading-[normal]"
                        style="font-family: 'Inter Display', Helvetica;">
                        Augment your
                    </p>
                    
                    <RotatingText :texts="words"
                        :mainClassName="`text-white w-fit font-medium text-white text-2xl text-center leading-[normal]`"
                        :staggerFrom="'last'" :initial="{ y: '100%' }" :animate="{ y: 0 }" :exit="{ y: '-120%' }"
                        :staggerDuration="0.025" :splitLevelClassName="'overflow-hidden pb-0.5 sm:pb-1 md:pb-1'"
                        :transition="{ type: 'spring', damping: 30, stiffness: 400 }" :rotationInterval="2000" />

                    <p class="w-fit font-medium text-[#ffffffb2] text-2xl text-center leading-[normal]"
                        style="font-family: 'Inter Display', Helvetica;">
                        with Diverz
                    </p>
                </div>
            </div>

            <!-- Button -->
            <Button
                class="w-[196px] h-auto items-center justify-center gap-2.5 px-6 py-3 rounded-[5px] bg-[linear-gradient(153deg,rgba(87,79,161,1)_0%,rgba(204,160,202,1)_100%)] hover:opacity-90 transition-opacity translate-y-[-1rem] animate-fade-in [--animation-delay:400ms]">
                <span class="w-fit font-semibold text-white text-base text-center leading-[normal] whitespace-nowrap"
                    style="font-family: 'Inter Display', Helvetica;">
                    Join our Alpha
                </span>
            </Button>
        </div>

        <!-- Image -->
        <img class="h-[541.23px] w-full max-w-[995.8px] rounded-[5px] object-cover px-4 translate-y-[-1rem] animate-fade-in [--animation-delay:600ms]"
            alt="Feature last plan" src="https://c.animaapp.com/mhalnqzadLBG4i/img/feature-1---last-plan-1-1.png" />
    </section>
</template>

<script setup lang="ts">
import { ref, onMounted, onBeforeUnmount } from "vue";
import Button from "~/components/ui/Button.vue";
import RotatingText from "../ui/RotatingText.vue";

const words = ["NetOps", "DevOps", "SysOps", "SycOps"];
const currentIndex = ref(0);
const currentWord = ref(words[currentIndex.value]);

let interval: ReturnType<typeof setInterval>;

onMounted(() => {
    interval = setInterval(() => {
        currentIndex.value = (currentIndex.value + 1) % words.length;
        currentWord.value = words[currentIndex.value];
    }, 2000);
});

onBeforeUnmount(() => {
    clearInterval(interval);
});
</script>
