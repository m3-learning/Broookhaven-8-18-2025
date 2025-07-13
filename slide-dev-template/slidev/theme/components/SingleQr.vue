<script setup>
import QrcodeVue from 'qrcode.vue' // ✅ Fix

const props = defineProps({
  value: {
    type: String,
    required: true,
  },
  size: {
    type: Number,
    default: 300,
  },
})
</script>

<template>
  <QrcodeVue :value="value" :size="size" level="H" />
</template>
