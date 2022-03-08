<template>
  <div id="app">
    <PentagonChart />
    <BarChartContainer />
  </div>
</template>

<script>
import PentagonChart from './components/pentagon/PentagonChart.vue';
import BarChartContainer from '@/components/bar/BarChartContainer';

export default {
  name: 'App',
  components: {
    PentagonChart,
    BarChartContainer,
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
