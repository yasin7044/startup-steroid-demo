<script setup>
import ListItem from '@/components/ListItem.vue'

defineProps({
  group: Object
})
</script>

<template>
  <div class="my-4 list-item-group">
    <ListItem v-if="group.title" :title="group.title" class="list-item-group__title" />
    <ListItem v-for="(item, i) in group.items" :key="i" v-bind="item" />
  </div>
</template>

<style >
.list-item-group {
  .list-item-group__title {
    .label {
      font-size: 16px;
    }
  }
}
</style>
