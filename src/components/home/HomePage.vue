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
      <BarChartContainer
        v-bind:user-data-props="userData"
        v-bind:company-data="selectedCompany"
        v-bind:company-name="companyName"
        v-bind:view-type="viewType"
      />
    </div>
  </div>
</template>

<script>
import PentagonChart from '../pentagon/PentagonChart.vue';
import SearchInput from './SearchInput.vue';
import SearchInfo from './SearchInfo.vue';
import MainHeader from './MainHeader.vue';
import BarChartContainer from '@/components/bar/BarChartContainer';
import companyDataJson from '../../assets/company.json';
import company from '../../assets/company.json';
import userData from '../../assets/user.json';

const userJsonData = [];
for (let key in userData.user) {
  userJsonData.push(userData.user[key]);
}

export default {
  name: 'HomePage',
  components: {
    PentagonChart,
    MainHeader,
    SearchInput,
    SearchInfo,
    BarChartContainer,
  },
  watch: {
    companyName: function () {
      const companyData = this.company[this.companyName];
      let chartScore = [];
      for (let key in companyData) {
        chartScore.push(companyData[key]);
      }
      this.companyJsonData = chartScore;
      this.selectedCompany = this.companyDataJson[this.companyName];
    },
    companyJsonData() {
      this.allView();
    },
  },
  methods: {
    allView() {
      this.isAll = true;
      this.isMe = false;
      this.isCompany = false;
      this.makeAllData();
      this.chartData.datasets.push(this.setPoint);
      this.viewType = 'isAll';
    },
    meView() {
      this.isAll = false;
      this.isMe = true;
      this.isCompany = false;
      this.makeMeData();
      this.chartData.datasets.push(this.setPoint);
      this.viewType = 'isMe';
    },
    componyView() {
      this.isAll = false;
      this.isMe = false;
      this.isCompany = true;
      this.makeCompanyData();
      this.chartData.datasets.push(this.setPoint);
      this.viewType = 'isCompany';
    },
    makeAllData() {
      this.chartData = {
        labels: this.setLabels,
        datasets: [this.meData, this.companyData],
      };
      this.chartData.datasets[1].data = this.companyJsonData;
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
      this.chartData.datasets[0].data = this.companyJsonData;
    },
  },
  data() {
    return {
      company: company,
      companyName: '',
      companyJsonData: [],
      isAll: false,
      isMe: true,
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

        data: userJsonData,
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

            data: [],
          },
          {
            label: '1',
            borderWidth: 2,
            borderColor: 'rgba(110, 60, 249, 1)',
            backgroundColor: 'rgba(110, 60, 249, 0.32)',
            pointRadius: 0,

            data: userJsonData,
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
      selectedCompany: {},
      companyDataJson,
      viewType: 'isMe',
    };
  },
};
</script>

<style>
.radar-chart {
  width: 90%;
  height: 600px;
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
  top: 35%;
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
