<script setup>
import NavItem from './NavItem.vue'
import { NAV_ITEMS } from '@/constants'

defineProps(['currentPage'])

const emit = defineEmits(['navigate'])
</script>

<template>
  <nav class="sticky bottom-0 z-10 bg-white">
    <ul class="flex items-center justify-around border-t">
      <NavItem
        v-for="(icon, page) in NAV_ITEMS"
        :key="page"
        v-bind:href="`#${page}`"
        :class="{ 'bg-gray-200 pointer-events-none': page == currentPage }"
        v-on:click="emit('navigate', page)"
      >
        <component v-bind:is="icon" class="h-6 w-6" /> {{ page }}
      </NavItem>
    </ul>
  </nav>
</template>
