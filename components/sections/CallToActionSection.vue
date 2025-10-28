<template>
    <section class="w-full flex flex-col items-center gap-[99px] bg-[#000000] py-[137px]">
        <div
            class="inline-flex w-full max-w-[700px] flex-col items-center gap-8 px-4 translate-y-[-1rem] animate-fade-in">
            <!-- Title -->
            <div class="flex flex-col items-center gap-3 w-full">
                <h1 class="w-fit font-semibold text-white text-[56px] text-center leading-[normal]"
                    style="font-family: 'Inter Display', Helvetica;">
                    An AI-native CLI Workspace
                </h1>

                <div
                    class="inline-flex items-center gap-2 flex-wrap justify-center translate-y-[-1rem] animate-fade-in [--animation-delay:200ms]">
                    <p class="w-fit font-medium text-[#ffffffb2] text-2xl text-center leading-[normal]"
                        style="font-family: 'Inter Display', Helvetica;">
                        Augment your
                    </p>

                    <div class="inline-flex items-center justify-center gap-2.5 px-0 py-[3px] rounded-[5px]">
                        <p class="w-fit font-medium text-white text-2xl text-center leading-[normal]"
                            style="font-family: 'Inter Display', Helvetica;">
                            NetOps,
                        </p>
                    </div>

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
import Button from "~/components/ui/Button.vue";
</script>
