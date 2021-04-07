<template>
  <div id="app">
    <div style="height: 800px; display: flex;">
      <calendar
        ref="calendar"
        :min-date="minDate"
        :select-date="dateList"
        :first-day-of-week="1"
        :showTitle="true"
        :isWeek="false"
        :showTerm="false"
        :mixinFestival="true"
        :multiple="true">
      </calendar>
    </div>
  </div>
</template>

<script>
import Calendar from './components/Calendar';

export default {
  name: 'App',
  components: {
    Calendar
  },
  data() {
    return {
      minDate: new Date(),
      dateList: [],
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
