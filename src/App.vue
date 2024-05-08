<script setup lang="ts">
import Navbar from '@/components/Layout/Navbar.vue'
</script>

<template>
  <Navbar />
  <div class="container px-4 py-4">
    <RouterView />
  </div>
</template>
