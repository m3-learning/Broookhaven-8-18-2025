<script setup>
import Layouttextbox from "../components/citation.vue"
import SlideNumber from "../components/SlideNumber.vue"

const props = defineProps({
  titleText: { type: String, default: 'Default Title' },
  subtitleText: { type: String, default: '' },
  image: { type: String, required: false },
  headerHeight: { type: [String, Number], default: 7.5 },
  subtitleHeight: { type: [String, Number], default: 7.5 },
  mainHeight: { type: [String, Number], default: 55 },
  textboxHeight: { type: [String, Number], default: 15 },
  spacerHeight: { type: [String, Number], default: 10 },
  reference: { type: String, default: ' d' },
})
</script>

<template>
  <div class="slidev-layout custom-layout">
    <!-- Header -->
    <div class="flex flex-col justify-center gap-2">
      <h1 class="text-5xl font-bold text-[#24527a] leading-tight m-0 text-left">{{ titleText }}</h1>
    </div>

    <div v-if="subtitleText" class="flex flex-col justify-center gap-2">
      <h2 class="text-2xl font-semibold text-[#2B90B6] leading-snug m-0 text-center">{{ subtitleText }}</h2>
    </div>

    <!-- Main Image Area -->
    <div class="flex justify-center items-center w-full h-full overflow-hidden">
      <div class="relative w-full h-full flex justify-center items-center">
        <img v-if="image"
             :src="image"
             class="max-w-full max-h-full object-contain rounded-2xl block" />
        <slot v-else />
      </div>
    </div>

    <!-- Text Content -->
    <div class="text-left text-base leading-tight">
      <slot name="text" />
    </div>

    <!-- Footer/Spacer -->
    <div class="flex items-center justify-center w-full">
      <Layouttextbox :reference="reference" />
    </div>
  </div>

  <!-- Slide Number Component -->
  <SlideNumber />
</template>

<style lang="postcss">
/* Kill Slidev injected borders and paddings */
:global(.slidev-layout) {
  @apply border-0 p-0 m-0 shadow-none !important;
}

/* Main layout grid */
.slidev-layout.custom-layout {
  @apply h-full w-full grid px-10 py-6 gap-4;
  background-image: url("../assets/full-branding.png");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
  grid-template-rows: v-bind('`${headerHeight}% ${subtitleHeight}% ${mainHeight}% ${textboxHeight}% ${spacerHeight}%`');
}
</style>
