<template>
  <BarChart :chart-data="data" :user-data="userData" :company-data="selectedCompany" :max-score="MAX_SCORE" />
</template>

<script>
import BarChart from './BarChart.vue';
import { userData, selectedCompany } from '@/assets/barData';
export default {
  name: 'BarChartContainer',
  components: {
    BarChart,
  },
  data() {
    return {
      MAX_SCORE: 10,
      personalityType: [
        ['적극성', '수동성'],
        ['자신감', '신중함'],
        ['책임감', '무심함'],
        ['개인 성향', '조직 성향'],
        ['수평사고', '위계사고'],
      ],
      userData,
      selectedCompany,
      data: { userData: userData, companyData: selectedCompany },
    };
  },
};
</script>

<style></style>
