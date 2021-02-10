<template>
  <section v-if="isAlternatingTuesday.status || manualShow.status">
    <div class="max-w-2xl mx-auto text-center pb-8 px-4 sm:pb-10 sm:px-6 lg:px-8">
      <h2
        class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl"
        @click="state.count++"
      >
        Yes, he is!
      </h2>
    </div>
    <picture class="flex justify-center">
      <source srcset="../assets/reginald.jpg">
      <img src="../assets/reginald.jpg" alt="This is Reginald. Everybody say 'Hi Reginald'">
    </picture>
  </section>
  <section v-else>
    <div class="max-w-3xl mx-auto text-center pb-8 px-4 sm:pb-10 sm:px-6 lg:px-8">
      <h2
        class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl"
        @click="state.count++"
      >
        No, unfortunately he is not.
      </h2>
    </div>
    <div class="max-w-3xl mx-auto text-center pt-8 px-4 sm:pt-10 sm:px-6 lg:px-8">
      <h2 class="text-3xl font-extrabold text-gray-900 dark:text-white sm:text-4xl">He will be back in <countdown :nextDate="nextDate" />.</h2>
    </div>
  </section>
</template>

<script setup>
  import { reactive, watch } from 'vue'
  import Countdown from './Countdown.vue'

  const getWeeksBetween = (d1, d2) => Math.round((d2 - d1) / (7 * 24 * 60 * 60 * 1000))

  const isDateAlternatingTuesday = date => {
    const originDate = new Date('January 22 2019')
    const weeksBetween = getWeeksBetween(originDate, date)
    const isTuesday = date.getDay() === 2
    const isAlternatingWeek = weeksBetween % 2 === 0
    return isTuesday && isAlternatingWeek
  }

  const isAlternatingTuesday = reactive({ status: isDateAlternatingTuesday(new Date()) })

  const getNextAlternatingTuesday = () => {
    const currentDate = new Date()
    const dayOfWeek = currentDate.getDay()
    const nextDate = new Date()
     if (dayOfWeek < 2) {
      nextDate.setDate(nextDate.getDate() + (2 - dayOfWeek))
    } else {
      nextDate.setDate(nextDate.getDate() + (9 - dayOfWeek))
    }
    if (!isDateAlternatingTuesday(nextDate)) {
      nextDate.setDate(nextDate.getDate() + 7)
    }

    return new Date(nextDate.getFullYear(), nextDate.getMonth(), nextDate.getDate())
  }

  const nextDate = getNextAlternatingTuesday()

  let manualShow = reactive({ status: false })
  const state = reactive({ count: 0 })
  watch(() => state.count, count => {
    if (count === 5) {
      manualShow.status = !manualShow.status
      state.count = 0
      console.log('toggled!')
    }
  })
</script>
