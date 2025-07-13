<script setup>
import { ref, defineProps } from 'vue'

const props = defineProps({
  node: Object
})

const isOpen = ref(false)
</script>

<template>
  <div class="pl-2">
    <div v-if="node.type === 'folder'" class="cursor-pointer" @click="isOpen = !isOpen">
      <span>{{ isOpen ? '📂' : '📁' }} {{ node.name }}</span>
    </div>
    <div v-else>
      <span>📄 {{ node.name }}</span>
    </div>

    <div v-if="node.children && isOpen" class="pl-4">
      <RecursiveFileTree
        v-for="(child, index) in node.children"
        :key="index"
        :node="child"
      />
    </div>
  </div>
</template>
