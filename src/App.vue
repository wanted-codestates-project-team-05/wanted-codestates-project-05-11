<template>
  <div id="app">
    <HomePage />
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
}

body {
  margin: 0;
}
</style>
