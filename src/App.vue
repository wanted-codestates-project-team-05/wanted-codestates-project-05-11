<template>
  <div id="app">
    <PentagonChart />
  </div>
</template>

<script>
import PentagonChart from './components/pentagon/PentagonChart.vue';

export default {
  name: 'App',
  components: {
    PentagonChart,
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
