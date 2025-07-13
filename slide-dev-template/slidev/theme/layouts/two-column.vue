<script setup>
import { computed } from 'vue'
import Layouttextbox from "../components/citation.vue"
import SlideNumber from "../components/SlideNumber.vue"

const props = defineProps({
  titleText: { type: String, default: 'Default Title' },
  leftHeading: { type: String, default: '' },
  rightHeading: { type: String, default: '' },
  leftImage: { type: String, default: '' },
  rightImage: { type: String, default: '' },
  headerHeight: { type: [String, Number], default: 7.5 },
  headingRowHeight: { type: [String, Number], default: 7.5 },
  mainHeight: { type: [String, Number], default: 55 },
  textboxHeight: { type: [String, Number], default: 15 },
  spacerHeight: { type: [String, Number], default: 10 },
  reference: { type: String, default: '' },
  columns: { type: Number, default: 2 },
})

// Compute dynamic grid layout
const gridTemplateRows = computed(() => {
  const header = props.headerHeight
  const hasHeadings = props.leftHeading.trim() !== '' || props.rightHeading.trim() !== ''
  const headingRow = hasHeadings ? props.headingRowHeight : 0
  const main = props.mainHeight + (hasHeadings ? 0 : props.headingRowHeight)
  const textbox = props.textboxHeight
  const spacer = props.spacerHeight

  return `${header}% ${headingRow}% ${main}% ${textbox}% ${spacer}%`
})

// Two-column layout
const twoColumnGrid = computed(() => `repeat(2, 1fr)`)
</script>

<template>
  <div class="slidev-layout custom-layout" :style="{ gridTemplateRows }">

    <!-- Title -->
    <div class="flex flex-col justify-center gap-2">
      <h1 class="title-large">{{ titleText }}</h1>
    </div>

    <!-- Heading Row (optional) -->
    <div class="main-grid" :style="{ gridTemplateColumns: twoColumnGrid }">
      <div class="flex items-center justify-center">
        <h2 v-if="leftHeading" class="text-2xl font-semibold text-[#2B90B6] leading-snug m-0 text-center">
          {{ leftHeading }}
        </h2>
      </div>
      <div class="flex items-center justify-center">
        <h2 v-if="rightHeading" class="text-2xl font-semibold text-[#2B90B6] leading-snug m-0 text-center">
          {{ rightHeading }}
        </h2>
      </div>
    </div>

    <!-- Main Two-Column Section -->
    <div class="main-grid" :style="{ gridTemplateColumns: twoColumnGrid }">
      
      <!-- Left Column -->
      <div class="flex flex-col justify-start items-center w-full h-full p-4 gap-4 overflow-hidden">
        <div v-if="leftImage" class="flex-grow flex justify-center items-center w-full h-full overflow-hidden">
          <img
            :src="leftImage"
            class="max-w-full max-h-full object-contain rounded-xl"
            style="height: 100%; max-height: 100%;"
          />
        </div>
        <div class="flex-shrink-0 w-full">
          <slot name="left" />
        </div>
      </div>

      <!-- Right Column -->
      <div class="flex flex-col justify-start items-center w-full h-full p-4 gap-4 overflow-hidden">
        <div v-if="rightImage" class="flex-grow flex justify-center items-center w-full h-full overflow-hidden">
          <img
            :src="rightImage"
            class="max-w-full max-h-full object-contain rounded-xl"
            style="height: 100%; max-height: 100%;"  
          />
        </div>
        <div class="flex-shrink-0 w-full">
          <slot name="right" />
        </div>
      </div>

    </div>

    <!-- Text Section -->
    <div class="text-left text-base leading-tight">
      <slot name="text" />
    </div>

    <!-- Footer -->
    <div class="flex items-center justify-center w-full">
      <Layouttextbox :reference="reference" />
    </div>

  </div>

  <!-- Move SlideNumber here, bottom left -->
  <div class="custom-slide-number">
      <SlideNumber />
</div>

</template>

<style lang="postcss">
:global(.slidev-layout) {
  @apply border-0 p-0 m-0 shadow-none !important;
}

.main-grid {
  display: grid;
  width: 100%;
  height: 100%;
  gap: 1rem;
}


  
  
</style>
