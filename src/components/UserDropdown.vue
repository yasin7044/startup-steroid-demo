<script setup>
import DAvatar from '@/components/DAvatar.vue'
import DBtnDropdown from '@/components/DBtnDropdown.vue'

const dropdownOpen = defineModel({
  type: Boolean,
  default: false
})
</script>

<template>
  <DBtnDropdown v-model="dropdownOpen" class="user-dropdown">
    <template #label>
      <div class="row items-center no-wrap">
        <DAvatar src="https://avatar.iran.liara.run/public/23" />
        <span class="user-dropdown__label ml-2">Administrator</span>
      </div>
    </template>

    <div class="p-2 column">
      <div class="cursor-pointer p-1">Developer</div>
      <div class="cursor-pointer p-1">Tester</div>
    </div>
  </DBtnDropdown>
</template>

<style lang="scss">
@media only screen and (max-width: 440px) {
  .user-dropdown__label {
    display: none;
  }
}
</style>
