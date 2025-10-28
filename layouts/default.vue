<template>
  <div class="bg-[#000000] overflow-hidden w-full relative max-w-[2400px] mx-auto">
    <!-- Header -->
    <header
      class="flex w-full items-center justify-between px-4 md:px-8 lg:px-16 xl:px-32 2xl:px-[200px] py-3 fixed top-0 left-0 right-0 z-50 backdrop-blur-[7.5px] backdrop-brightness-[100%] bg-[linear-gradient(180deg,rgba(0,0,0,0.38)_0%,rgba(0,0,0,0)_100%)] animate-fade-in relative">
      <img class="relative w-[134px] h-[29.97px] md:w-[100px] md:h-[22px]" alt="Infraxcode dark"
        src="https://c.animaapp.com/mhalnqzadLBG4i/img/infraxcode-dark-2-1.svg" />

      <!-- Desktop Nav -->
      <nav class="hidden lg:inline-flex items-center gap-12 relative flex-[0_0_auto]">
        <a v-for="(link, index) in navLinks" :key="index" :href="link.href"
          class="mt-[-1.00px] font-semibold text-white text-base whitespace-nowrap relative w-fit text-center tracking-[0] leading-[normal] transition-opacity hover:opacity-80">
          {{ link.label }}
        </a>
      </nav>

      <!-- Desktop Button -->
      <button
        class="hidden md:inline-flex items-center justify-center gap-2.5 px-4 py-2 relative flex-[0_0_auto] rounded-[5px] bg-[linear-gradient(153deg,rgba(87,79,161,1)_0%,rgba(204,160,202,1)_100%)] border-0 hover:opacity-90 transition-opacity">
        <span
          class="text-base relative w-fit mt-[-1.00px] font-semibold text-white text-center tracking-[0] leading-[normal] whitespace-nowrap">
          Join our Alpha
        </span>
      </button>

      <!-- Mobile Menu Button -->
      <button
        @click="isMobileMenuOpen = !isMobileMenuOpen"
        class="lg:hidden inline-flex items-center justify-center p-2 relative flex-[0_0_auto] text-white hover:opacity-80 transition-opacity"
        aria-label="Toggle mobile menu">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path v-if="!isMobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
          <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
    </header>

    <!-- Mobile Nav Menu -->
    <nav
      v-if="isMobileMenuOpen"
      class="lg:hidden fixed top-0 left-0 w-full h-screen bg-[#000000] bg-opacity-95 backdrop-blur-[7.5px] z-[60] flex flex-col items-center justify-center gap-8 py-8 overflow-y-auto">
      <button
        @click="isMobileMenuOpen = false"
        class="absolute top-4 right-4 inline-flex items-center justify-center p-2 text-white hover:opacity-80 transition-opacity"
        aria-label="Close mobile menu">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
      </button>
      <a v-for="(link, index) in navLinks" :key="index" :href="link.href"
        class="font-semibold text-white text-xl whitespace-nowrap relative w-fit text-center tracking-[0] leading-[normal] transition-opacity hover:opacity-80 py-2">
        {{ link.label }}
      </a>
      <button
        @click="isMobileMenuOpen = false"
        class="inline-flex mx-auto items-center justify-center gap-2.5 px-8 py-3 self-stretch rounded-[5px] bg-[linear-gradient(153deg,rgba(87,79,161,1)_0%,rgba(204,160,202,1)_100%)] border-0 hover:opacity-90 transition-opacity w-full max-w-sm">
        <span
          class="text-lg relative w-fit font-semibold text-white text-center tracking-[0] leading-[normal] whitespace-nowrap">
          Join our Alpha
        </span>
      </button>
    </nav>

    <!-- Page content -->
    <main class="relative w-full pt-16 lg:pt-0">
      <slot />
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const isMobileMenuOpen = ref(false);

const navLinks = [
  { label: "Home", href: "#" },
  { label: "Features", href: "#features" },
  { label: "Contact", href: "#contact" },
];
</script>