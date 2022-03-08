<template>
  <div class="wrapper">
    <header class="header">
      <h4 class="sub">MY RESULT</h4>
      <h1 class="result">나의 결과는?</h1>
    </header>
    <ul class="container">
      <li class="row" v-for="(scoreType, index) in scoreTypes" :key="scoreType">
        <span>
          <span
            class="section"
            :style="[userData[scoreType] >= 5 && { color: '#417341', fontWeight: 700, fontSize: '12px' }]"
          >
            <span class="bigNum">{{ userData[scoreType] }}</span>
            <span>/{{ MAX_SCORE }}</span>
          </span>
          <span :style="[userData[scoreType] >= 5 && { color: '#29ba41', fontWeight: 700, fontSize: '12px' }]"
            >{{ personalityType[index][0] }}
          </span>
        </span>
        <span>
          <span
            class="section"
            :style="[userData[scoreType] >= 5 && { color: '#417341', fontWeight: 700, fontSize: '12px' }]"
            >{{ personalityType[index][1] }}</span
          >
          <span :style="[userData[scoreType] >= 5 && { color: '#29ba41', fontWeight: 700, fontSize: '12px' }]">
            <span class="bigNum">{{ MAX_SCORE - userData[scoreType] }}</span>
            <span>/{{ MAX_SCORE }}</span></span
          >
        </span>
      </li>
      <BarChart
        class="Chart"
        :chart-data="data"
        :user-data="userData"
        :company-data="selectedCompany"
        :max-score="MAX_SCORE"
      />
    </ul>
  </div>
</template>

<script>
import BarChart from './BarChart.vue';
import { userData, selectedCompany } from '@/assets/barData';

const scoreTypes = [...Object.keys(userData)];

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
      scoreTypes,
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
  width: 360px;
  height: 985px;
  margin: 0 auto;
  border: 1px solid var(--color-black);
}
.header {
  position: absolute;
  width: 328px;
  height: 118px;
  left: 16px;
  top: 465px;
  background: var(--color-white);
}
.sub {
  position: absolute;
  width: 328px;
  height: 17px;
  left: 0px;
  top: 16px;
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
  position: absolute;
  width: 328px;
  height: 59px;
  left: 0px;
  top: 43px;
  font-family: Roboto;
  font-style: normal;
  font-weight: bold;
  font-size: 36px;
  line-height: 140%;
  text-align: center;
  color: var(--color-black);
}
.Chart {
  position: absolute;
  height: 220px;
  width: 140px;
}
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: 583px;
  height: 220px;
  width: 100%;
}
.row {
  width: 320px;
  height: 23px;
  margin: 7px;
  display: flex;
  justify-content: space-between;
  font-size: 10px;
  font-weight: 600;
}
.section {
  padding-right: 25px;
}
.bigNum {
  font-size: 14px;
  font-weight: 900;
}
</style>
