<script setup>
import { ref, defineProps } from 'vue'

const props = defineProps({
  node: Object
})

const isOpen = ref(false)
</script>

<template>
  <div class="border rounded-lg bg-white/5 backdrop-blur-sm p-2">
    <!-- Header -->
    <div
      v-if="node.type === 'folder'"
      class="cursor-pointer"
      @click="isOpen = !isOpen"
      :style="{ fontFamily: 'var(--slidev-font-body)' }"
    >
      <span>{{ isOpen ? '📂' : '📁' }} {{ node.name }}</span>
    </div>
    <div
      v-else
      :style="{ fontFamily: 'var(--slidev-font-body)' }"
    >
      <span>📄 {{ node.name }}</span>
    </div>

    <!-- Scrollable Tree Body -->
    <div
      v-if="node.children && isOpen"
      class="pl-4 mt-2 max-h-[400px] overflow-y-auto pr-2 border-l border-dashed border-gray-400"
    >
      <RecursiveFileTree
        v-for="(child, index) in node.children"
        :key="index"
        :node="child"
      />
    </div>
  </div>
</template>
