<template>
  <div id="app">
    <HomePage />
    <BarChartContainer />
  </div>
</template>

<script>
import HomePage from './components/home/HomePage.vue';
import BarChartContainer from '@/components/bar/BarChartContainer';

export default {
  name: 'App',
  components: {
    HomePage,
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

body {
  margin: 0;
}
</style>
