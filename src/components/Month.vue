<template>
  <div>
    <div>{{ month.month + 1 }}月</div>
    <div class="flex flex-justify-evenly">
      <div>日</div>
      <div>一</div>
      <div>二</div>
      <div>三</div>
      <div>四</div>
      <div>五</div>
      <div>六</div>
    </div>
    <div class="flex flex-wrap w-210px">
      <div class="w-30px" v-for="e in month.firstDayWeekday"></div>
      <div class="w-30px" v-for="day in month.days" :key="day">{{ day }}</div>
    </div>
  </div>
</template>
<script setup>
import daysjs from 'dayjs'
defineProps({
  month: Object,
})
</script>
