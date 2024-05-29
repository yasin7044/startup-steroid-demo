<script setup>
import RecordCard from '@/components/RecordCard.vue'
import DocumentsTable from '@/components/DocumentsTable.vue'
import DDrawer from '@/components/DDrawer.vue'
import NavBar from '@/components/NavBar.vue'
import { shallowRef } from 'vue'
import RightDrawer from '@/components/RightDrawer.vue'
import RecentWorkflowChart from '@/components/RecentWorkflowChart.vue'

const items = [
  {
    title: 'Document',
    icon: 'fluent:document-folder-16-regular',
    value: '146.000'
  },
  {
    title: 'Contact',
    icon: 'ri:contacts-book-upload-line',
    value: '1400'
  },
  {
    title: 'Email',
    icon: 'mi:email',
    value: '150.700'
  }
]

const drawer = shallowRef(false)
const rightDrawer = shallowRef(false)
</script>

<template>
  <div class="layout">
    <NavBar @drawerClick="drawer = !drawer" v-model:right-drawer="rightDrawer" />
    <DDrawer v-model="drawer" />
    <RightDrawer v-model="rightDrawer" />

    <div class="page-container">
      <main class="px-5 pb-5">
        <div class="space-y-4">
          <div class="row items-center d-col-gutter-md">
            <div v-for="item in items" :key="item" class="col col-xs-12 col-sm-4 col-md-6 col-lg-4">
              <RecordCard :item="item" class="" />
            </div>
          </div>

          <div class="row d-col-gutter-md">
            <div class="col-md-12 col-xs-12 col-sm-6 col-lg-6">
              <RecentWorkflowChart />
            </div>
            <div class="col-md-12 col-xs-12 col-sm-6 col-lg-6">
              <RecentWorkflowChart type="bar" />
            </div>
          </div>

          <DocumentsTable />
        </div>
      </main>
    </div>
  </div>
</template>

<style lang="scss">
.layout {
  position: relative;
  height: 100%;
  width: 100%;
  overflow: hidden;
}

.page-container {
  &::-webkit-scrollbar {
    display: none;
  }

  position: absolute;
  top: 87px;
  left: 300px;
  right: 250px;
  bottom: 0;
  overflow: auto;
}

@media only screen and (max-width: 1020px) {
  .page-container {
    left: 0;
    right: 0;
  }
}
</style>
