<template>
    <footer
      v-if="reference"
      class="mt-auto flex justify-center w-full text-fuchsia-700 dark:text-white"
    >
      <p v-if="reference" class="mb-0 text-center">{{ reference }}</p>
    </footer>
  </template>
  
  <script setup lang="ts">
  const props = defineProps({
    reference: {
      type: String,
    },
  });
  </script>