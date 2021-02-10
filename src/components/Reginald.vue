<template>
  <h1>Reginald is {{ isAlternatingTuesday ? '': 'not ' }}here :{{ isAlternatingTuesday ? ')': '(' }}</h1>

  <p><button @click="toDarkMode">dark mode</button></p>
  <p><button @click="toLightMode">light mode</button></p>
</template>

<script setup>
  const toDarkMode = () => window.document.documentElement.classList.add('dark')
  const toLightMode = () => window.document.documentElement.classList.remove('dark')

  const getWeeksBetween = (d1, d2) => Math.round((d2 - d1) / (7 * 24 * 60 * 60 * 1000))

  const originDate = new Date('January 22 2019')
  const currentDate = new Date()
  const weeksBetween = getWeeksBetween(originDate, currentDate)

  const isTuesday = currentDate.getDay() === 2
  const isAlternatingWeek = weeksBetween % 2 === 0
  const isAlternatingTuesday = isTuesday && isAlternatingWeek
</script>
