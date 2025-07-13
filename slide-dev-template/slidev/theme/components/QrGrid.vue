<script setup>
import QrcodeVue from 'qrcode.vue'
import { computed } from 'vue'

const props = defineProps({
  items: {
    type: Array,
    required: true,
    // [{ title: string, url: string }]
  },
  columns: {
    type: Number,
    default: 3,
  },
})

// Break items into rows of size `columns`
const rows = computed(() => {
  const result = []
  for (let i = 0; i < props.items.length; i += props.columns) {
    result.push(props.items.slice(i, i + props.columns))
  }
  return result
})
</script>

<template>
  <div class="flex flex-col items-center justify-center h-full gap-6 px-6">
    <div
      v-for="(row, rowIndex) in rows"
      :key="rowIndex"
      class="flex justify-center gap-8 w-full"
    >
      <div
        v-for="(item, i) in row"
        :key="i"
        class="flex flex-col items-center text-center p-2"
      >
      <QrcodeVue
  :value="item.url"
  :size="128"
  level="M"
  foreground="#07294D"
  background="transparent"
/>
        <p>{{ item.title }}</p>
      </div>
    </div>
  </div>
</template>
