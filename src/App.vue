<template>
  <div id="app">
    <PentagonChart />
    <BarChartContainer :user-data-props="userData" :company-data="selectedCompany"/>
  </div>
</template>

<script>
import PentagonChart from './components/pentagon/PentagonChart.vue';
import BarChartContainer from '@/components/bar/BarChartContainer';
import { userData, selectedCompany } from '@/assets/barData';

export default {
  name: 'App',
  components: {
    PentagonChart,
    BarChartContainer,
  },
  data() {
    return {
      userData,
      selectedCompany,
    };
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
