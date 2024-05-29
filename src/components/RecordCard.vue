<script setup>
import DIcon from '@/components/DIcon.vue'
import { Icon } from '@iconify/vue'

defineProps({
  item: Object
})
</script>

<template>
  <div class="card rounded">
    <div class="row justify-between header">
      <span class="title">{{ item.title }}</span>
      <DIcon :name="item.icon" />
    </div>

    <div class="body mt-4 mb-4">
      <h2>{{ item.value }}</h2>
    </div>

    <div class="footer">
      <div class="row items-center">
        <div class="text-positive row items-center">
          <Icon icon="material-symbols:trending-up-rounded"  />&nbsp;<span>17%</span>
        </div>
        &nbsp; &nbsp; Since last week
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  padding: 1rem;
  background-color: white;

  .title {
    font-weight: 600;
  }

  .body {
    h2 {
      font-weight: bold;
    }
  }
}

.material-symbols-outlined {
  font-variation-settings:
    'FILL' 0,
    'wght' 400,
    'GRAD' 0,
    'opsz' 24;
}
</style>
