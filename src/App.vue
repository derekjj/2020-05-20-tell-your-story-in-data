<template lang="pug">
  #app
    .row
      .col-12 
        TimeLine
    .row
      .col-12 Random Charts
    .row
      .col-12 
        LineChart
    .row
      .col-12 
        ColumnChart
</template>

<script>
import TimeLine from './components/TimeLine.vue'
import ColumnChart from './components/ColumnChart.vue'
import LineChart from './components/LineChart.vue'

export default {
  name: 'App',
  components: {
    TimeLine,
    ColumnChart,
    LineChart
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
