<script setup>
import DAvatar from '@/components/DAvatar.vue'
import DBtnDropdown from '@/components/DBtnDropdown.vue'

const dropdownOpen = defineModel({
  type: Boolean,
  default: false
})
</script>

<template>
  <div class="row items-center no-wrap">
    <DAvatar src="https://avatar.iran.liara.run/public/23" />
    <DBtnDropdown v-model="dropdownOpen" label="Administrator" >
      <div class="p-2 column" >
        <div class="cursor-pointer p-1">Developer</div>
        <div class="cursor-pointer p-1">Tester</div>
      </div>
    </DBtnDropdown>
  </div>
</template>

<style scoped></style>
