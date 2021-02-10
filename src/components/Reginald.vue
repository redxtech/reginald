<template>
  <h1>Reginald is not here :(</h1>

  <button @click="state.count++">count is: {{ state.count }}</button>
</template>

<script setup>
import { reactive } from 'vue'

const state = reactive({ count: 0 })
</script>
