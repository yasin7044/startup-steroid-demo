<script setup>
import ListItem from '@/components/ListItem.vue'
import ListItemGroup from '@/components/ListItemGroup.vue'

const drawerOpen = defineModel({
  type: Boolean,
  default: false
})

const groups = [
  {
    title: 'Management',
    items: [
      {
        title: 'Document',
        icon: 'fluent:document-folder-16-regular'
      },
      {
        title: 'Contact',
        icon: 'ri:contacts-book-upload-line'
      },
      {
        title: 'Prospect',
        icon: 'mdi:pot-outline'
      },
      {
        title: 'Workflow',
        icon: 'hugeicons:recycle-03'
      }
    ]
  },
  {
    title: 'Connection',
    items: [
      {
        title: 'Chat Integration',
        icon: 'heroicons:chat-bubble-oval-left'
      },
      {
        title: 'Marketing Automation',
        icon: 'octicon:briefcase-16'
      },
      {
        title: 'Email Integration',
        icon: 'mi:email'
      }
    ]
  },
  {
    title: 'Customer',
    items: [
      {
        title: 'Transaction',
        icon: 'clarity:two-way-arrows-line'
      },
      {
        title: 'Maintenance',
        icon: 'clarity:settings-line'
      }
    ]
  }
]

</script>

<template>
  <div
    class="px-5 py-10 d-drawer d-drawer__mobile"
    :class="{ 'd-drawer__mobile-open': drawerOpen }"
  >
    <!--      <div id="d-drawer-btn" class="d-drawer-btn__close row items-center justify-end">-->
    <!--        <DBtn @click="toggleDrawer">-->
    <!--          <Icon icon="material-symbols:close" />-->
    <!--        </DBtn>-->
    <!--      </div>-->
    <h1 class="title ml-6">CRM.io</h1>

    <div class="list mt-5 text-white">
      <ListItem icon="hugeicons:dashboard-square-02" title="Dashboard" active />

      <template v-for="(group, i) in groups" :key="i">
        <hr v-if="i" style="border-color: #45597e" class="ml-4" />
        <ListItemGroup :group="group" />
      </template>
    </div>
  </div>
</template>

<style lang="scss">
$drawer-width: 300px;

.d-drawer {
  width: $drawer-width;
  background-color: #041535;
  z-index: 1;
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;

  & > .title {
    color: #e58562;
    font-style: italic;
    font-weight: 600;
  }

  .list {
    .list-item-group {
      .list-item {
        opacity: 0.7;
      }

      .list-item-group__title {
        opacity: 0.5;
      }
    }
  }
}

@keyframes drawer-position {
  from {
    left: calc($drawer-width * -1);
  }
  to {
    left: 0;
  }
}

#d-drawer-btn {
  display: none;
}

@media only screen and (max-width: 1020px) {
  .d-drawer__mobile {
    position: fixed;
    height: 100%;
    top: 83px;
    left: calc($drawer-width * -1);
    bottom: 0;
    transition: left 0.5s ease-in-out;
    overflow: auto;
  }

  .d-drawer__mobile-open {
    left: 0;
  }

  #d-drawer-btn {
    display: block;
  }

  .d-drawer-btn__close {
    display: flex !important;

    .d-btn {
      background-color: transparent;
      color: white;
      padding: 0;
    }
  }
}
</style>
