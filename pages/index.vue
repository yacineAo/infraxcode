<template>
  <div>
    <section class="relative w-full translate-y-[-1rem] animate-fade-in [--animation-delay:200ms]">
      <CallToActionSection />
    </section>

    <section class="relative w-full translate-y-[-1rem] animate-fade-in [--animation-delay:400ms]">
      <SectionsFeaturesSection />
    </section>

    <!-- <section class="relative w-full translate-y-[-1rem] animate-fade-in [--animation-delay:600ms]">
      <SectionsTestimonialsSection />
    </section> -->
  </div>
</template>

<script setup lang="ts">
import CallToActionSection from "~/components/sections/CallToActionSection.vue";
</script>
