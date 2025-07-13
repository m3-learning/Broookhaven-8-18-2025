<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'
import { useNav } from '@slidev/client'

const route = useRoute()
const nav = useNav() // Slidev's internal navigation controller

// Compute the current page
const currentPage = computed(() => {
  if (route.query.page) {
    return parseInt(route.query.page)
  } else {
    const path = route.path
    const number = parseInt(path.replace('/', ''))
    return isNaN(number) ? 1 : number
  }
})

// Total number of slides (Slidev knows this)
const totalPages = computed(() => nav.total)
</script>

<template>
  <div class="fixed bottom-4 right-6 text-2xl text-gray-600 opacity-70 select-none pointer-events-none" style="z-index: 9999">
    {{ currentPage }} / {{ totalPages }}
  </div>
</template>
