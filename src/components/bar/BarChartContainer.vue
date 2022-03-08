<template>
  <div class="wrapper">
    <header class="header">
      <h4 class="sub">MY RESULT</h4>
      <h1 class="result">나의 결과는?</h1>
    </header>
    <ul class="container">
      <li class="row" v-for="(scoreType, index) in scoreTypes" :key="scoreType">
        <span class="section">
          <span :style="[userData[scoreType] >= 5 && { color: '#417341', fontWeight: 700, fontSize: '12px' }]">
            <span class="bigNum">{{ userData[scoreType] }}</span>
            <span>/{{ MAX_SCORE }}</span>
          </span>
          <span :style="[userData[scoreType] >= 5 && { color: '#29ba41', fontWeight: 700, fontSize: '12px' }]"
            >{{ personalityType[index][0] }}
          </span>
        </span>
        <span class="section">
          <span :style="[userData[scoreType] >= 5 && { color: '#417341', fontWeight: 700, fontSize: '12px' }]">{{
            personalityType[index][1]
          }}</span>
          <span :style="[userData[scoreType] >= 5 && { color: '#29ba41', fontWeight: 700, fontSize: '12px' }]">
            <span class="bigNum">{{ MAX_SCORE - userData[scoreType] }}</span>
            <span>/{{ MAX_SCORE }}</span></span
          >
        </span>
      </li>
      <BarChart class="Chart" v-bind:chart-data="chartData" v-bind:company-name="selectedCompanyName" />
    </ul>
  </div>
</template>

<script>
import BarChart from './BarChart.vue';

const MAX_SCORE = 10;

export default {
  name: 'BarChartContainer',
  components: {
    BarChart,
  },
  props: {
    userDataProps: Object,
    companyData: Object,
    companyName: String,
  },
  watch: {
    companyName: function () {
      this.selectedCompanyName = this.companyName;
      this.chartData = { ...this.chartData, companyData: this.companyData };
      console.log(this.companyData, 'barChartContainer');
    },
  },
  data() {
    return {
      MAX_SCORE,
      personalityType: [
        ['적극성', '수동성'],
        ['자신감', '신중함'],
        ['책임감', '무심함'],
        ['개인 성향', '조직 성향'],
        ['수평사고', '위계사고'],
      ],
      userData: this.userDataProps,
      chartData: { userData: this.userDataProps, companyData: this.companyData, maxScore: MAX_SCORE },
      scoreTypes: [...Object.keys(this.userDataProps)],
      selectedCompanyName: this.companyName,
    };
  },
};
</script>

<style>
:root {
  --color-black: #121212;
  --color-white: #ffffff;
}

.wrapper {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 320px;
  max-width: 800px;
  margin: 0 auto;
}

.header {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  position: absolute;
  top: 0px;
  height: 118px;
}

.sub {
  height: 17px;
  font-family: Agenor;
  font-style: normal;
  font-weight: bold;
  font-size: 12px;
  line-height: 140%;
  text-align: center;
  letter-spacing: 0.32em;
  color: var(--color-black);
}

.result {
  height: 59px;
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 36px;
  line-height: 140%;
  text-align: center;
  color: var(--color-black);
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  bottom: 0px;
  height: 220px;
  width: 100%;
}

.row {
  width: 95%;
  height: 25px;
  margin: 6px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-size: 10px;
  font-weight: 600;
}

.Chart {
  position: absolute;
  height: 202px;
  width: 45%;
  bottom: 3px;
}

.section {
  width: 25%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.bigNum {
  font-size: 14px;
  font-weight: 900;
}
</style>
