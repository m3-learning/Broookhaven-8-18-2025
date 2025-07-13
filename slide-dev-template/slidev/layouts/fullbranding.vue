<template>
  <div class="w-full h-screen relative overflow-hidden">
    <!-- Background Image -->
    <div
      class="absolute inset-0 bg-no-repeat bg-center"
      :style="{
        backgroundImage: `url('/assets/full-branding.png')`,
        backgroundSize: backgroundFit,
        backgroundColor: backgroundColor,
      }"
    />

    <!-- Foreground Content -->
    <div class="relative z-10 p-6 md:p-12 text-white h-full">
      <slot />
    </div>

    <!-- Debug Info -->
    <div class="absolute bottom-0 left-0 z-50 bg-black bg-opacity-70 text-white text-xs px-2 py-1 font-mono">
      background: /assets/full-branding.png<br>
      fit: {{ backgroundFit }}
    </div>
  </div>
</template>

<script setup lang="ts">
const backgroundFit = $slidev.nav.currentPage?.meta?.backgroundFit ?? 'cover'
const backgroundColor = $slidev.nav.currentPage?.meta?.backgroundColor ?? 'white'
</script>

<style scoped>
:global(html), :global(body), :global(#app) {
  height: 100%;
  margin: 0;
}
</style>
