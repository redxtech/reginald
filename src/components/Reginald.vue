<template>
  <section v-if="isAlternatingTuesday">
    <div class="max-w-2xl mx-auto text-center pb-8 px-4 sm:pb-10 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl">Yes, he is!</h2>
    </div>
    <picture class="flex justify-center">
      <source srcset="../assets/reginald.jpg">
      <img src="../assets/reginald.jpg" alt="This is Reginald. Everybody say 'Hi Reginald'">
    </picture>
  </section>
  <section v-else>
    <div class="max-w-3xl mx-auto text-center pb-8 px-4 sm:pb-10 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl">No, unfortunately he is not.</h2>
    </div>
    <div class="max-w-3xl mx-auto text-center pt-8 px-4 sm:pt-10 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl">He will be back in <countdown :nextDate="nextDate" />.</h2>
    </div>
  </section>
</template>

<script setup>
  import Countdown from './Countdown.vue'
  const getWeeksBetween = (d1, d2) => Math.round((d2 - d1) / (7 * 24 * 60 * 60 * 1000))

  const originDate = new Date('January 22 2019')
  const currentDate = new Date()
  const weeksBetween = getWeeksBetween(originDate, currentDate)

  const isTuesday = currentDate.getDay() === 2
  const isAlternatingWeek = weeksBetween % 2 === 0
  const isAlternatingTuesday = isTuesday && isAlternatingWeek

  const nextDate = new Date()
  nextDate.setDate(nextDate.getDate() + 7)
</script>
