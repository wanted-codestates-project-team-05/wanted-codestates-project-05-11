<template>
  <div id="home">
    <main-header />
    <search-info v-model="companyName" />
    <search-input v-model="companyName" />
    <div class="radar-chart">
      <PentagonChart :chartdata="chartData" :options="options" />
      <div class="bg-img"></div>
      <div class="button-wrapper">
        <button v-bind:class="['button-style', { active: isAll }]" @click="allView()">
          <img alt="all" src="../../assets/all.png" width="13" height="13" />
          모두
        </button>
        <button v-bind:class="['button-style', { active: isMe }]" @click="meView()">
          <img alt="all" src="../../assets/me.png" width="10" height="10" />
          본인
        </button>
        <button v-bind:class="['button-style', { active: isCompany }]" @click="componyView()">
          <img alt="all" src="../../assets/company.png" width="10" height="10" />
          회사
        </button>
      </div>
      <BarChartContainer v-bind:user-data-props="userData" v-bind:company-data="selectedCompany" />
    </div>
  </div>
</template>

<script>
import PentagonChart from '../pentagon/PentagonChart.vue';
import SearchInput from './SearchInput.vue';
import SearchInfo from './SearchInfo.vue';
import MainHeader from './MainHeader.vue';
import BarChartContainer from '@/components/bar/BarChartContainer';
import companyData from '../../assets/company.json';
import userData from '../../assets/user.json';

export default {
  name: 'HomePage',
  components: {
    PentagonChart,
    MainHeader,
    SearchInput,
    SearchInfo,
    BarChartContainer,
  },
  methods: {
    allView() {
      this.isAll = true;
      this.isMe = false;
      this.isCompany = false;
      this.makeAllData();
      this.chartData.datasets.push(this.setPoint);
    },
    meView() {
      this.isAll = false;
      this.isMe = true;
      this.isCompany = false;
      this.makeMeData();
      this.chartData.datasets.push(this.setPoint);
    },
    componyView() {
      this.isAll = false;
      this.isMe = false;
      this.isCompany = true;
      this.makeCompanyData();
      this.chartData.datasets.push(this.setPoint);
    },
    makeAllData() {
      this.chartData = {
        labels: this.setLabels,
        datasets: [this.meData, this.companyData],
      };
    },
    makeMeData() {
      this.chartData = {
        labels: this.setLabels,
        datasets: [this.meData],
      };
    },
    makeCompanyData() {
      this.chartData = {
        labels: this.setLabels,
        datasets: [this.companyData],
      };
      this.chartData.datasets[0].data = [2, 7, 4, 8, 9];
    },
  },
  data() {
    return {
      companyName: '',
      isAll: true,
      isMe: false,
      isCompany: false,
      setPoint: {
        backgroundColor: 'rgba(244, 244, 244, 0.32)',
        borderColor: '#B2B2B2',
        borderWidth: 1,
        pointBackgroundColor: [
          'rgba(237, 168, 154, 0.7)',
          'rgba(182, 197, 248, 0.7)',
          'rgba(164, 214, 227, 0.7)',
          'rgba(238, 184, 207, 0.7)',
          'rgba(183, 220, 171, 0.7)',
        ],
        pointBorderColor: ['#EDA89A', '#B6C5F8', '#A4D6E3', '#EEB8CF', '#B7DCAB'],
        pointRadius: 18,
        data: [10, 10, 10, 10, 10],
      },
      setLabels: [
        ['적극적인', 'Aggressive', ''],
        [' 자신있는', 'Confident', ''],
        ['', '  책임있는', 'Responsible'],
        ['', '개인주의', 'Indivisual'],
        ['수평적인 ', 'Horizontal', ''],
      ],
      meData: {
        label: '1',
        borderWidth: 2,
        borderColor: 'rgba(110, 60, 249, 1)',
        backgroundColor: 'rgba(110, 60, 249, 0.32)',
        pointRadius: 0,

        data: [5, 7, 5, 6, 2],
      },
      companyData: {
        label: '2',
        borderWidth: 2,
        borderColor: 'rgba(255, 193, 74, 1)',
        backgroundColor: 'rgba(255, 193, 74, 0.32)',
        pointRadius: 0,

        data: [],
      },
      chartData: {
        labels: [
          ['적극적인', 'Aggressive', ''],
          [' 자신있는', 'Confident', ''],
          ['', '  책임있는', 'Responsible'],
          ['', '개인주의', 'Indivisual'],
          ['수평적인 ', 'Horizontal', ''],
        ],
        datasets: [
          {
            label: '2',
            borderWidth: 2,
            borderColor: 'rgba(255, 193, 74, 1)',
            backgroundColor: 'rgba(255, 193, 74, 0.32)',
            pointRadius: 0,

            data: [1, 5, 4, 2, 6],
          },
          {
            label: '1',
            borderWidth: 2,
            borderColor: 'rgba(110, 60, 249, 1)',
            backgroundColor: 'rgba(110, 60, 249, 0.32)',
            pointRadius: 0,

            data: [5, 7, 5, 6, 2],
          },
          {
            backgroundColor: 'rgba(244, 244, 244, 0.32)',
            borderColor: '#B2B2B2',
            borderWidth: 1,
            pointBackgroundColor: [
              'rgba(237, 168, 154, 0.7)',
              'rgba(182, 197, 248, 0.7)',
              'rgba(164, 214, 227, 0.7)',
              'rgba(238, 184, 207, 0.7)',
              'rgba(183, 220, 171, 0.7)',
            ],
            pointBorderColor: ['#EDA89A', '#B6C5F8', '#A4D6E3', '#EEB8CF', '#B7DCAB'],
            pointRadius: 18,
            data: [10, 10, 10, 10, 10],
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: false,
          //position: 'bottom',
        },
        tooltips: {
          enabled: false,
        },
        scale: {
          gridLines: {
            borderDash: [5, 5],
          },
          angleLines: {},
          ticks: {
            display: false,
            beginAtZero: true,
            max: 10,
            min: 0,
            stepSize: 2.5,
          },
          pointLabels: {
            fontFamily: 'Noto Sans',
            fontStyle: 'bold',
            fontColor: 'black',
            fontSize: 12,
            lineHeight: 1.5,
          },
        },
        enabled: true,
        hover: false,
        layout: {
          padding: 10,
        },
        elements: {
          point: {
            hoverRadius: '18',
          },
        },
      },
      userData: userData.user,
      selectedCompany: companyData['KAKAO'],
    };
  },
};
</script>

<style>
.radar-chart {
  width: 400px;
  height: 400px;
  margin: 0 auto;
  position: relative;
}
.button-wrapper {
  width: 90%;
  min-width: 328px;
  height: 45px;
  display: flex;
  justify-content: center;
  align-items: center;
  margin: 0 auto;
  background-color: #f2f2f2;
  border-radius: 4px;
}
.button-style {
  width: 33.333%;
  height: 100%;
  display: flex;
  flex-direction: row;
  justify-content: center;
  align-items: center;
  border: 1px solid #f2f2f2;
  font-size: 12px;
  cursor: pointer;
  border-radius: 4px;
  background-color: #f2f2f2;
  color: #727272;
}
img {
  margin-right: 6px;
}
.active {
  background-color: #fff;
  color: #121212;
}
.bg-img {
  position: absolute;
  left: 50%;
  top: 54%;
  transform: translate(-50%, -50%);
  background-image: url('../../assets/chart-bg.png');
  background-size: 54px 54px;
  width: 54px;
  height: 54px;
  border-radius: 50%;
  z-index: 10;
}
#home {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  width: 100%;
  max-width: 800px;
  display: flex;
  flex-direction: column;
}
</style>
