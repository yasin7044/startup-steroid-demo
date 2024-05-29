<script setup>
import { Icon } from '@iconify/vue'

defineProps({
  name: String
})
</script>

<template>
  <span class="d-icon">
    <Icon :icon="name"  class="m-2" color="teal" />
  </span>
</template>

<style scoped>
.d-icon {
  border-radius: 50%;
  background-color: #bef8f8;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;

  svg {
    width: 24px;
    height: 24px;
  }
}
</style>
