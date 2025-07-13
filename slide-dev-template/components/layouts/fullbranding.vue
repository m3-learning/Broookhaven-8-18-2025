<template>
  <div class="w-full h-screen relative overflow-hidden">

    <!-- Background Image Layer -->
    <div
      class="absolute inset-0 bg-no-repeat bg-center"
      :style="{
        backgroundImage: background ? `url('${background}')` : undefined,
        backgroundSize: backgroundFit,
        backgroundColor: backgroundColor,
      }"
    />

    <!-- Foreground Slot -->
    <div class="relative z-10 p-6 md:p-12 text-white h-full">
      <slot />
    </div>

    <!-- Debug Output -->
    <div class="absolute bottom-0 left-0 z-50 bg-black bg-opacity-70 text-white text-xs px-2 py-1 font-mono">
      background: {{ background }}<br>
      fit: {{ backgroundFit }}
    </div>

  </div>
</template>
<script setup lang="ts">
import { useSlide } from '@slidev/client'

const { meta } = useSlide()
const background = meta.background ?? ''
const backgroundFit = meta.backgroundFit ?? 'cover'
const backgroundColor = meta.backgroundColor ?? 'black'
</script>
const backgroundColor = meta.backgroundColor ?? 'black'
</script>

<style scoped>
:global(html), :global(body), :global(#app) {
  height: 100%;
  margin: 0;
}
</style>
