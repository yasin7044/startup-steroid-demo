<script setup>
import { Icon } from '@iconify/vue'
import DAvatar from '@/components/DAvatar.vue'

defineProps({
  title: String,
  icon: String,
  avatar: String,
  subtitle: String,
  active: {
    type: Boolean,
    default: false
  }
})
</script>

<template>
  <div class="list-item row px-6 py-3 items-center" :class="{ 'list-item__active': active }">
    <Icon v-if="icon" :icon="icon" class="mr-2" />
    <DAvatar v-else-if="avatar" :src="avatar" class="mr-4" />
    <div class="column ">
      <div class="title">{{ title }}</div>
      <small>{{subtitle}}</small>
    </div>
  </div>
</template>

<style lang="scss">
.list-item {
  flex-wrap: nowrap;
  border-radius: 14px;

  .title {
    font-size: 14px;
    font-weight: inherit;
  }

  .iconify {
    font-weight: 600;
  }
}

.list-item__active {
  background-color: #3e64aa;
  font-weight: bold;
}
</style>
