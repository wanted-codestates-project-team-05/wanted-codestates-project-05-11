<template>
  <div class="wrapper">
    <header class="header">
      <h4 class="title1">MY RESULT</h4>
      <h1 class="title2">나의 결과는?</h1>
    </header>
    <ul class="container">
      <li v-for="(list, index) in userObj" v-bind:key="list" class="itemRow">
        <span>
          <span
            :style="[data.user[list] >= 5 && { color: '#417341', fontWeight: 700, fontSize: '12px' }]"
            class="item1"
          >
            <span class="BigNum">{{ data.user[list] }}</span>
            <span>/{{ MAX_SCORE }}</span>
          </span>
          <span :style="[data.user[list] >= 5 && { color: '#29ba41', fontWeight: 700, fontSize: '12px' }]"
            >{{ personalityArray[index][0] }}
          </span>
        </span>
        <span>
          <span
            :style="[data.user[list] >= 5 && { color: '#417341', fontWeight: 700, fontSize: '12px' }]"
            class="item1"
            >{{ personalityArray[index][1] }}</span
          >
          <span :style="[data.user[list] >= 5 && { color: '#29ba41', fontWeight: 700, fontSize: '12px' }]">
            <span class="BigNum">{{ MAX_SCORE - data.user[list] }}</span>
            <span>/{{ MAX_SCORE }}</span></span
          >
        </span>
      </li>
      <BarChart class="Chart" :chartValue="data" :name="this.name" />
    </ul>
  </div>
</template>

<script>
import BarChart from './BarChart.vue';
import Data from '../../assets/data.json';
const userObj = [...Object.keys(Data.user)];
const MAX_SCORE = 10;
const personalityArray = [
  ['적극성', '수동성'],
  ['자신감', '신중함'],
  ['책임감', '무심함'],
  ['개인 성향', '조직 성향'],
  ['수평사고', '위계사고'],
];
export default {
  name: 'BarChartWrapper',
  components: {
    BarChart,
  },
  data() {
    return {
      MAX_SCORE,
      userObj,
      personalityArray,
      data: Data,
      name: 'SAMSUNG',
    };
  },
  mounted() {
    // console.log(this.data.user.aggressive);
  },
};
</script>

<style>
.wrapper {
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 360px;
  height: 985px;
  margin: 0 auto;
  border: 1px solid black;
}
.header {
  position: absolute;
  width: 328px;
  height: 118px;
  left: 16px;
  top: 465px;
  background: #ffffff;
}
.title1 {
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
  color: #121212;
}
.title2 {
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
  color: #121212;
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
.itemRow {
  width: 320px;
  height: 23px;
  margin: 7px;
  display: flex;
  justify-content: space-between;
  font-size: 11px;
  font-weight: 700;
}
.item1 {
  padding-right: 25px;
}
.BigNum {
  font-size: 14px;
  font-weight: 900;
}
</style>
