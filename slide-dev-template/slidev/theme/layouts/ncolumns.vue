<script setup>
import { computed } from 'vue'
import Layouttextbox from "../components/citation.vue"
import SlideNumber from "../components/SlideNumber.vue"

const props = defineProps({
  titleText: { type: String, default: 'Default Title' },
  images: { type: Array, default: () => [] },
  titles: { type: Array, default: () => [] },
  titleClicks: { type: Array, default: () => [] },
  columns: { type: Number, default: 2 },
  columnWidths: { type: Array, default: () => [] },
  reference: { type: String, default: '' },
  headerHeight: { type: [String, Number], default: 7.5 },
  headingRowHeight: { type: [String, Number], default: 7.5 },
  mainHeight: { type: [String, Number], default: 55 },
  textboxHeight: { type: [String, Number], default: 15 },
  spacerHeight: { type: [String, Number], default: 10 },
  showBorders: { type: Boolean, default: false },
  roundedEdges: { type: Boolean, default: true }
})

const gridTemplateRows = computed(() => {
  const header = props.headerHeight
  const headingRow = props.titles.length > 0 ? props.headingRowHeight : 0
  const main = props.mainHeight + (props.titles.length > 0 ? 0 : props.headingRowHeight)
  const textbox = props.textboxHeight
  const spacer = props.spacerHeight
  return `${header}% ${headingRow}% ${main}% ${textbox}% ${spacer}%`
})

const gridColumns = computed(() => {
  if (props.columnWidths.length === props.columns) {
    return props.columnWidths.map(w => `${w}fr`).join(' ')
  } else {
    return `repeat(${props.columns}, 1fr)`
  }
})
</script>

<template>
  <div class="slidev-layout custom-layout" :style="{ gridTemplateRows }">
    <!-- Title -->
    <div class="flex flex-col justify-center gap-2 ml-[-1rem]">
      <div class="title-large">{{ titleText }}</div>
    </div>

    <!-- Column Headings -->
    <div class="columns-headings" :style="{ gridTemplateColumns: gridColumns }">
      <h2
        v-for="(title, index) in titles"
        :key="`heading-${index}`"
        v-click="titleClicks[index]"
      >
        {{ title }}
      </h2>
    </div>

    <!-- Main Content Section -->
    <div class="columns-main" :style="{ gridTemplateColumns: gridColumns }">
      <div
        v-for="(col, index) in columns"
        :key="`col-${index}`"
        class="flex flex-col items-start justify-start p-4 gap-2 w-full h-full overflow-auto"
        :class="{ 'border-2 border-black': showBorders }"
      >
        <div class="w-full h-full flex flex-col justify-center items-center">
          <img
            v-if="images[index]"
            :src="images[index]"
            class="max-w-full max-h-full object-contain"
            :style="{
              maskImage: 'radial-gradient(circle at center, black 100%, transparent 100%)',
              WebkitMaskImage: 'radial-gradient(circle at center, black 100%, transparent 100%)',
              borderRadius: roundedEdges ? '1rem' : '0',
              overflow: 'hidden'
            }"
            alt=""
            v-click="titleClicks[index]"
          />
          <div v-else v-click="titleClicks[index]" class="w-full h-full">
            <slot :name="`col${index}`" />
          </div>
        </div>
      </div>
    </div>

    <!-- Textbox Content -->
    <div class="text-left text-base leading-tight px-6" :class="{ 'border-2 border-black': showBorders }">
      <slot name="text" />
    </div>

    <!-- Reference -->
    <div class="absolute bottom-[10px] left-1/2 -translate-x-1/2 leading-none">
      <span class="slidev-layout-reference">{{ reference }}</span>
    </div>
  </div>

  <!-- Slide Number -->
  <div class="custom-slide-number">
    <SlideNumber />
  </div>
</template>

<style lang="postcss">
.custom-ncolumns {
  @apply h-full w-full relative;
  display: grid;
  gap: 0.5rem;
}

.columns-headings {
  display: grid;
  width: 100%;
  text-align: center;
  align-items: center;
  justify-items: center;
  padding: 0 1rem;
}

.columns-main {
  display: grid;
  width: 100%;
  height: 100%;
  gap: 1rem;
  padding: 0 1rem;
  align-items: start;
}
</style>
