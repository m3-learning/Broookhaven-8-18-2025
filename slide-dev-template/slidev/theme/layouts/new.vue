<script setup>
import { computed } from 'vue'
import LayoutTextbox from "../components/citation.vue"
import SlideNumber from "../components/SlideNumber.vue"

const props = defineProps({
  titleText: { type: String, default: 'Default Title' },
  subtitleText: { type: String, default: '' },
  heights: {
    type: Object,
    default: () => ({
      header: 7.5,
      subtitle: 7.5,
      main: 55,
      textbox: 15,
      spacer: 10
    })
  },
  reference: { type: String, default: '' },
})

const gridTemplateRows = computed(() => {
  const { header, subtitle, main, textbox, spacer } = props.heights
  return props.subtitleText.trim()
    ? `${header}% ${subtitle}% ${main}% ${textbox}% ${spacer}%`
    : `${header}% 0% ${main + subtitle}% ${textbox}% ${spacer}%`
})
</script>

<template>
  <div class="slidev-layout custom-layout" :style="{ gridTemplateRows }">
    <!-- Header -->
    <header class="flex-center">
      <h1 class="title-large text-left">{{ titleText }}</h1>
    </header>

    <!-- Subtitle (conditionally hidden but always rendered) -->
    <section class="flex-center overflow-hidden">
      <h2
        class="subtitle text-2xl font-semibold text-[#2B90B6] text-center"
        :class="{ 'invisible h-0': !subtitleText.trim() }"
      >
        {{ subtitleText }}
      </h2>
    </section>

    <!-- Main Image Area -->
    <section class="relative flex-center overflow-hidden">
      <slot />
    </section>

    <!-- Text Content -->
    <section class="text-content text-base leading-tight">
      <slot name="text" />
    </section>

    <!-- Footer -->
    <footer class="flex-center">
      <LayoutTextbox :reference="reference" />
    </footer>
  </div>

  <SlideNumber class="custom-slide-number" />
</template>

<style lang="postcss">
.flex-center {
  @apply flex items-center justify-center;
}

.text-content {
  @apply text-left px-2;
}

:global(.slidev-layout) {
  @apply border-0 p-0 m-0 shadow-none;
}

.slidev-layout.custom-layout {
  @apply grid w-full h-full gap-4 px-10 py-6;
  grid-template-rows: v-bind(gridTemplateRows);
  background-image: url("../assets/Drexel-background.svg");
  background-repeat: no-repeat;
  background-position: center;
  background-size: cover;
}
</style>
