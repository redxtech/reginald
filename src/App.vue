<template>
  <!-- This example requires Tailwind CSS v2.0+ -->
  <div class="container mx-auto px-4 sm:px-6 lg:px-8">
    <!-- This example requires Tailwind CSS v2.0+ -->
    <div class="bg-white dark:bg-gray-800">
      <div class="max-w-7xl mx-auto py-16 px-4 sm:py-24 sm:px-6 lg:px-8">
        <div class="text-center">
          <p class="mt-1 text-4xl font-extrabold text-gray-900 dark:text-white sm:text-5xl sm:tracking-tight lg:text-6xl">Is Reginald Here Today?</p>
          <p class="max-w-xl mt-5 mx-auto text-xl text-gray-500 dark:text-gray-400">Remember, reginald is only here on alternating Tuesdays.</p>
        </div>
      </div>
    </div>
    <reginald />
  </div>
</template>

<script setup>
import Reginald from './components/Reginald.vue'

// This starter template is using Vue 3 experimental <script setup> SFCs
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
</script>

<style>
  #app {
    @apply min-h-screen bg-white dark:bg-gray-800;
  }
</style>
