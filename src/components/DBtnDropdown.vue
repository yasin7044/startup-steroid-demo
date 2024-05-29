<script setup>
import DMenu from '@/components/DMenu.vue'
import DBtn from '@/components/DBtn.vue'
import { Icon } from '@iconify/vue'

defineProps({
  label: String
})

const menuOpen = defineModel({
  type: Boolean,
  default: false
})
</script>

<template>
  <DMenu v-model="menuOpen">
    <template #activator="{ props, open }">
      <DBtn v-bind="props">
        <div class="row items-center justify-center">
          <span class="mr-2" >{{ label }}</span>
          <Icon
            icon="mdi:chevron-down"
            class="d-btn-dropdown__arrow"
            :class="{ 'rotate-180': open }"
          />
        </div>
      </DBtn>
    </template>

    <slot />
  </DMenu>
</template>

<style scoped>
.d-btn-dropdown__arrow {
  transition: transform 0.28s;
}
</style>
