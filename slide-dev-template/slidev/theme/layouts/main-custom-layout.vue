<script setup>
import { computed } from 'vue'
import Layouttextbox from "../components/citation.vue"
import SlideNumber from "../components/SlideNumber.vue"

const props = defineProps({
  titleText: { type: String, default: 'Default Title' },
  subtitleText: { type: String, default: '' },
  headerHeight: { type: [String, Number], default: 7.5 },
  subtitleHeight: { type: [String, Number], default: 7.5 },
  mainHeight: { type: [String, Number], default: 55 },
  textboxHeight: { type: [String, Number], default: 15 },
  spacerHeight: { type: [String, Number], default: 10 },
  reference: { type: String, default: '' },
})

const gridTemplateRows = computed(() => {
  const header = props.headerHeight
  const subtitle = props.subtitleText.trim() === '' ? 0 : props.subtitleHeight
  const textbox = props.textboxHeight
  const spacer = props.spacerHeight
  const main = props.mainHeight + (props.subtitleText.trim() === '' ? props.subtitleHeight : 0)

  return `${header}% ${subtitle}% ${main}% ${textbox}% ${spacer}%`
})
</script>

<template>
  <div class="slidev-layout custom-layout" :style="{ gridTemplateRows }">
    <!-- Header -->
    <div class="flex flex-col justify-center gap-2 ml-[-1rem]">
      <div class="title-large">{{ titleText }}</div>
    </div>

    <!-- Subtitle (conditionally hidden but always rendered) -->
    <div 
      class="flex flex-col justify-center gap-2"
      :style="{ visibility: subtitleText.trim() ? 'visible' : 'hidden' }"
    >
      <h2 class="text-2xl font-semibold text-[#2B90B6] leading-snug m-0 text-center">{{ subtitleText }}</h2>
    </div>

    <!-- Main Image Area -->
    <div class="flex justify-center items-center w-full h-full overflow-hidden">
      <div class="relative w-full h-full flex justify-center items-center">
        <slot />
      </div>
    </div>

    <!-- Text Content -->
    <div class="text-left text-base leading-tight">
      <slot name="text" />
    </div>

    <!-- Footer/Spacer -->
    <div class="flex items-center justify-center w-full">
    </div>
  </div>

  <div class="custom-slide-number">
    <SlideNumber />
  </div>

    <!-- Footer/Spacer -->
    <div class="absolute bottom-[10px] left-1/2 -translate-x-1/2 leading-none">
    <span class="slidev-layout-reference">{{ reference }}</span>
    </div>
</template>

<style lang="postcss">
:global(.slidev-layout) {
  @apply border-0 p-0 m-0 shadow-none !important;
}

.slidev-layout.custom-layout {
  @apply h-full w-full grid px-10 py-6 gap-4;
  background-image: url("../assets/Drexel-background.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
</style>
