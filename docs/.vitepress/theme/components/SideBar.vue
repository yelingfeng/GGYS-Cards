<script setup lang="ts">
import { defineProps } from 'vue'
import NavLinks from './NavLinks.vue'
import SideBarLinks from './SideBarLinks.vue'
// import Slugs from './Slugs.vue'

defineProps({
  open: { type: Boolean, required: true }
})
</script>

<template>
  <aside class="sidebar" :class="{ open }">
    <NavLinks class="nav" />

    <slot name="sidebar-top" />

    <SideBarLinks />

    <slot name="sidebar-bottom" />
  </aside>
  <ClientOnly>
    <Slugs />
  </ClientOnly>
</template>

<style scoped>
.sidebar {
  position: fixed;
  top: var(--header-height);
  bottom: 0;
  left: 0;
  z-index: var(--z-index-sidebar);
  /* border-right: 1px solid var(--c-divider); */
  width: var(--sidebar-width);
  background-color: var(--c-bg);
  overflow-y: auto;
  transform: translateX(-100%);
  transition: transform 0.25s ease;
}

@media (min-width: 720px) {
  .sidebar {
    transform: translateX(0);
  }
}

/* @media (min-width: 960px) {
  .sidebar {
    width: 20rem;
  }
} */

.sidebar.open {
  transform: translateX(0);
  box-shadow: 0 0 5px rgb(10 16 20 / 12%);
}

.nav {
  display: block;
}

@media (min-width: 720px) {
  .nav {
    display: none;
  }
}
</style>
