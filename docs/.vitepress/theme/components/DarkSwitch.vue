<script setup lang="ts">
import { useToggle } from '@vueuse/core'
import { isDark } from '../composables/dark'
const toggle = useToggle(isDark)
</script>

<template>
  <button aria-label="Toggle Theme" class="nav-btn m-0 p-0" @click="toggle">
    <ri-moon-fill v-show="isDark" />
    <ri-sun-fill v-show="!isDark" />
  </button>
</template>
