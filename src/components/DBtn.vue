<script setup>
defineOptions({
  inheritAttrs: false
})

defineProps({
  label: String
})
</script>

<template>
  <button class="no-outline d-btn py-2 px-3 row items-center" v-bind="$attrs">
    <slot>
      {{ label }}
    </slot>
  </button>
</template>

<style>
.d-btn {
  border: none;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 500;
  cursor: pointer;
}
</style>
