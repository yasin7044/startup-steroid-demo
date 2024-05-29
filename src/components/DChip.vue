<script setup>
import { computed } from 'vue'

const props = defineProps({
  label: String,
  size: {
    type: String,
    default: '12px'
  }
})

const theme = computed(() => {
  const values = {
    fontSize: props.size,
  }
  switch (props.label.toLowerCase()) {
    case 'send':
      values.color = 'green'
      values.backgroundColor = `#caffca`
      break;
    default:
      values.color = '#FFA500'
      values.backgroundColor = '#fde7c1'
  }
  return values
})
</script>

<template>
  <div class="px-5 py-2 text-center rounded" :style="theme" style=" font-weight: 600">
    {{label}}
  </div>
</template>

<style scoped>

</style>