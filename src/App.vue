<template>
  <div id="app">
    <HomePage />
    <PentagonChart />
    <div class="bg-img"></div>
  </div>
</template>

<script>
import HomePage from './components/home/HomePage.vue';
import PentagonChart from './components/pentagon/PentagonChart.vue';

export default {
  name: 'App',
  components: {
    HomePage,
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
.bg-img {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  background-image: url('./assets/chart-bg.png');
  background-size: 54px 54px;
  width: 54px;
  height: 54px;
  border-radius: 50%;
  z-index: 10;
}
</style>
