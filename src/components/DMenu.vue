<script setup>
import { computed } from 'vue'

defineOptions({
  inheritAttrs: false
})

const menuOpen = defineModel({
  type: Boolean,
  default: false
})

function toggleMenu() {
  menuOpen.value = !menuOpen.value
}

const activatorProps = computed(() => {
  return {
    onClick: toggleMenu
  }
})
</script>

<template>
  <div class="menu">
    <slot name="activator" :props="activatorProps" :open="menuOpen" />
    <Transition name="fade">
      <div v-if="menuOpen" class="menu-content rounded" v-bind="$attrs" @click="toggleMenu">
        <slot>
          <div style="padding: 10px"></div>
        </slot>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
.menu {
  position: relative;
  display: inline-block;
}

.menu-content {
  background-color: white;
  box-shadow:
    0 3px 5px -1px rgba(0, 0, 0, 0.2),
    0 6px 10px rgba(0, 0, 0, 0.14),
    0 1px 18px rgba(0, 0, 0, 0.12);
  position: absolute;
  z-index: 999;
}
</style>
