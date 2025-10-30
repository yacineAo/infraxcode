<template>
    <footer class="flex flex-col w-full items-start gap-16 px-4 md:px-[200px] py-[72px] border-t [border-top-style:solid] border-[#ffffff52]
           bg-[linear-gradient(179deg,rgba(22,22,23,1)_0%,rgba(22,22,23,0)_100%)]">
        <!-- Top section -->
        <div class="flex flex-col md:flex-row items-start justify-between w-full gap-10">
            <!-- Brand description -->
            <div
                class="flex flex-col md:w-[302px] items-start gap-6 translate-y-[-1rem] animate-fade-in [--animation-delay:0ms]">
                <img class="w-[177px] h-[39.59px]" alt="Infraxcode dark"
                    src="https://c.animaapp.com/mhalnqzadLBG4i/img/infraxcode-dark-2.svg" />

                <p
                    class="self-stretch [font-family:'Inter_Display-Regular',Helvetica] font-normal text-white text-sm tracking-[0] leading-[normal]">
                    Diverz is the AI-powered workspace that gives network and
                    infrastructure engineers developer-grade productivity; safe, fast,
                    and vendor-smart
                </p>
            </div>

            <!-- Navigation / contact / legal -->
            <nav class="md:inline-flex md:flex-row flex-col flex items-start justify-end md:gap-20 gap-10">
                <!-- Navigation links -->
                <div
                    class="flex flex-col w-[66px] items-start gap-6 translate-y-[-1rem] animate-fade-in [--animation-delay:200ms]">
                    <ul class="inline-flex flex-col items-start justify-center gap-4">
                        <li v-for="(link, index) in navigationLinks" :key="index">
                            <a href="#"
                                class="[font-family:'Inter_Display-Medium',Helvetica] font-medium text-[#ffffffcc] text-sm text-center tracking-[0] leading-[normal] hover:text-white transition-colors">
                                {{ link.label }}
                            </a>
                        </li>
                    </ul>
                </div>

                <!-- Contact info -->
                <div
                    class="inline-flex flex-col items-start justify-center gap-6 translate-y-[-1rem] animate-fade-in [--animation-delay:400ms]">
                    <ul class="inline-flex flex-col items-start gap-[19px]">
                        <li v-for="(item, index) in contactInfo" :key="index" class="inline-flex items-center gap-1.5">
                            <component :is="item.icon" class="w-5 h-5 text-[#ffffffcc]" />
                            <span
                                class="[font-family:'Inter_Display-Medium',Helvetica] font-medium text-[#ffffffcc] text-sm tracking-[0] leading-[normal]">
                                {{ item.text }}
                            </span>
                        </li>
                    </ul>
                </div>

                <!-- Legal links -->
                <div
                    class="inline-flex flex-col items-start justify-center gap-6 translate-y-[-1rem] animate-fade-in [--animation-delay:600ms]">
                    <ul class="inline-flex flex-col items-start gap-[19px]">
                        <li v-for="(link, index) in legalLinks" :key="index">
                            <a href="#"
                                class="[font-family:'Inter_Display-Medium',Helvetica] font-medium text-[#ffffffcc] text-sm text-right tracking-[0] leading-[21px] whitespace-nowrap hover:text-white transition-colors">
                                {{ link.label }}
                            </a>
                        </li>
                    </ul>
                </div>
            </nav>
        </div>

        <!-- Bottom section -->
        <div
            class="flex flex-col md:flex-row items-center justify-between w-full translate-y-[-1rem] animate-fade-in [--animation-delay:800ms] gap-4">
            <p
                class="[font-family:'Inter_Display-Medium',Helvetica] font-medium text-[#ffffffcc] text-sm tracking-[0] leading-[21px] whitespace-nowrap">
                2025 Diverz. All Rights Reserved
            </p>

            <div class="flex w-[104px] items-center justify-end gap-4">
                <a v-for="(icon, index) in socialIcons" :key="index" href="#"
                    class="hover:opacity-80 transition-opacity">
                    <img class="w-5 h-5" :alt="icon.alt" :src="icon.src" />
                </a>
            </div>
        </div>
    </footer>
</template>

<script setup>
import { Mail, MapPin, Phone } from "lucide-vue-next";

const navigationLinks = [
    { label: "Home" },
    { label: "Features" },
    { label: "Contact" },
];

const contactInfo = [
    {
        icon: Mail,
        text: "contact@diverz.com",
    },
    {
        icon: Phone,
        text: "000000000000",
    },
    {
        icon: MapPin,
        text: "Address",
    },
];

const legalLinks = [
    { label: "Terms and conditions" },
    { label: "Privacy policy" },
];

const socialIcons = [
    {
        src: "https://c.animaapp.com/mhalnqzadLBG4i/img/vector-5.svg",
        alt: "Social media",
    },
    {
        src: "https://c.animaapp.com/mhalnqzadLBG4i/img/social-icon.svg",
        alt: "Social media",
    },
    {
        src: "https://c.animaapp.com/mhalnqzadLBG4i/img/social-icon-1.svg",
        alt: "Social media",
    },
];
</script>
