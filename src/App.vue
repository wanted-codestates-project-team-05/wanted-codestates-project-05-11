<template>
  <div id="app">
    <BarChartWrapper />
  </div>
</template>

<script>
// import PentagonChart from './components/pentagon/PentagonChart.vue';
import BarChartWrapper from './components/bar/BarChartWrapper.vue';

export default {
  name: 'App',
  components: {
    // PentagonChart,
    BarChartWrapper,
  },
};
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
