<script setup>
import { Icon } from '@iconify/vue'
import UserDropdown from '@/components/UserDropdown.vue'
import DBtn from '@/components/DBtn.vue'
import { shallowRef } from 'vue'

defineEmits(['drawer-click'])

const rightDrawer = defineModel('rightDrawer', {
  type: Boolean,
  default: false
})
const userDropdown = shallowRef(false)

function onRightDrawerClick() {
  rightDrawer.value = !rightDrawer.value
  userDropdown.value = false
}
</script>

<template>
  <nav class="navbar p-5" id="navbar">
    <div class="row items-center">
      <div id="d-drawer-btn" class="d-drawer-btn">
        <DBtn @click="$emit('drawer-click')" >
          <Icon icon="ei:navicon" />
        </DBtn>
      </div>
      <div>
        <h1 class="title">Overview</h1>
      </div>
    </div>

    <div class="row no-wrap space-x-5 items-center">
      <div id="d-drawer-btn" style="margin: 0 !important;">
        <DBtn @click="onRightDrawerClick" >
          <Icon icon="mdi:recent" />
        </DBtn>
      </div>
      <Icon icon="lets-icons:bell" />
      <UserDropdown v-model="userDropdown" @click="rightDrawer = false" />
    </div>
  </nav>
</template>

<style lang="scss">
.navbar {
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: fixed;
  top: 0;
  left: 300px;
  right: 0;
  z-index: 100;
  background-color: rgb(239, 239, 239);

  .title {
    font-size: 1.7rem;
    font-weight: bold;
  }
}


@media only screen and (max-width: 1020px) {
  .navbar {
    padding-left: 10px;
    padding-right: 10px;
    left: 0;
  }
}

#d-drawer-btn {
  .d-btn {
    padding-left: 0;
    padding-right: 10px;
  }
}
</style>
