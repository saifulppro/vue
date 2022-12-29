<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <div class="container mx-auto">
    <nav class="flex gap-4 bg-green-400 text-yellow-50 p-4">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>


  <RouterView />
</template>

<style scoped>

</style>
