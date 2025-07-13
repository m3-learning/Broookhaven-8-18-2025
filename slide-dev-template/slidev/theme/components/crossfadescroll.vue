<!-- components/ScrollableImages.vue -->
<script setup>
const props = defineProps({
  images: { type: Array, required: true },
})
</script>

<template>
  <div class="relative w-full h-full overflow-x-auto overflow-y-hidden whitespace-nowrap p-4 scroll-smooth">
    <img
      v-for="(src, idx) in images"
      :key="src"
      :src="src"
      class="inline-block h-full max-h-[70vh] mr-4 object-contain transition-transform duration-300 hover:scale-105"
      alt="Scrollable image"
    />
  </div>
</template>

