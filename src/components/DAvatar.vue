<script setup>
defineOptions({
  inheritAttrs: false
})

</script>

<template>
  <img v-bind="$attrs" class="d-avatar" />
</template>

<style scoped>
.d-avatar {
  width: 42px;
  height: 42px;
  border-radius: 50%;
}
</style>