<script setup>
import ListItemGroup from '@/components/ListItemGroup.vue'

const drawerOpen = defineModel({
  type: Boolean,
  default: false
})
const groups = [
  {
    title: 'Popular Product',
    items: [
      {
        title: 'Gadget Converter',
        subtitle: '$250',
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      },
      {
        title: 'Lens Camera',
        subtitle: '$50',
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      },
      {
        title: 'Airpods',
        subtitle: '$100',
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      },
      {
        title: 'Macbook',
        subtitle: '$999',
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      }
    ]
  },
  {
    title: 'Chat',
    items: [
      {
        title: 'Debra Young',
        subtitle: "How's my product?" ,
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      },
      {
        title: 'Dorothy Collins',
        subtitle: 'How was the meeting',
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      },
      {
        title: 'Chris Jordan',
        subtitle: 'How employee performance',
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      },
      {
        title: 'Denise Murphy',
        subtitle: 'How was the meeting',
        avatar: 'https://wallpapers.com/images/high/plain-black-background-gb7ds9afc2g1j0cp.webp'
      }
    ]
  }
]
</script>

<template>
  <div class="d-right-drawer column rounded d-right-drawer__mobile " :class="{ 'd-right-drawer__mobile-open': drawerOpen }">
    <ListItemGroup v-for="(group, i) in groups" :key="i" :group="group" class="mb-10"/>
  </div>
</template>

<style lang="scss" >
$right-drawer-width: 250px;

.d-right-drawer {
  min-width: $right-drawer-width;
  width: $right-drawer-width;
  position: fixed;
  top: 87px;
  right: 0;
  background-color: white;
  padding-top: 0.5rem;
  padding-bottom: 0.5rem;
  z-index: -1;

  .list-item {
    padding-top: 0.5rem;
    padding-bottom: 0.5rem;
  }

  .list-item-group {
    margin-top: 0;
  }

  .title {
    font-weight: 600;
  }
}


@media only screen and (max-width: 1020px) {
  .d-right-drawer__mobile {
    position: fixed;
    box-shadow:
      0 3px 5px -1px rgba(0, 0, 0, 0.2),
      0 6px 10px rgba(0, 0, 0, 0.14),
      0 1px 18px rgba(0, 0, 0, 0.12);
    right: calc($right-drawer-width * -2);
    transition: right 0.5s ease-in-out;
    z-index: 1;
  }

  .d-right-drawer__mobile-open {
    right: 0;
  }
}
</style>
