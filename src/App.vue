<script setup>
import Month from './components/Month.vue'
import daysjs from 'dayjs'
import objectSupport from 'dayjs/plugin/objectSupport'
daysjs.extend(objectSupport)
const year = 2024
const months = Array.from({ length: 12 }, (_, i) => i)
const getDaysInMonth = (month) => daysjs({ year, month }).daysInMonth()
const getMonethDayInfo = (month) => {
  const days = getDaysInMonth(month)
  const firstDay = daysjs({ year, month, day: 1 }).day()
  return { month, days, firstDay }
}
const yearMonths = months.map((month) => ({
  month,
  days: getDaysInMonth(month),
  firstDay: daysjs({ year, month, day: 1 }).day(),
  firstDayWeekday: daysjs({ year, month, day: 1 }).day(),
}))
console.log(`🦖   ~ yearMonths ~ yearMonths:`, yearMonths)
</script>

<template>
  <div>
    <h1>Calendar</h1>
    <div class="flex flex-wrap gap-50px">
      <Month v-for="month in yearMonths" :key="month.month" :month="month" />
    </div>
  </div>
</template>

<style scoped></style>
