<script>
import { HorizontalBar } from 'vue-chartjs';

export default {
  extends: HorizontalBar,
  props: {
    chartValue: Object,
    name: String,
  },

  data() {
    return {
      options: {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: false,
        },
        scales: {
          yAxes: [
            {
              gridLines: {
                display: false,
              },
              ticks: {
                fontSize: 20,
                beginAtZero: true,
              },
            },
          ],
          xAxes: [
            {
              gridLines: {
                display: false,
              },
              ticks: {
                display: false,
                min: -10,
                max: 10,
                stepSize: 20,
              },
            },
          ],
        },
      },
    };
  },

  methods: {
    getData(value, name) {
      let user = value.user && Object.values(value.user);
      let userInfo = user.map((i) => (i >= 5 || i === 0 ? i * -1 : 10 - i));

      let company = value.company && Object.values(value.company[name]);
      let companyInfo = company.map((i) => (i >= 5 || i === 0 ? i * -1 : 10 - i));
      const data = {
        labels: ['', '', '', '', ''],
        datasets: [
          {
            label: 'User',
            backgroundColor: '#6E3CF9',
            barPercentage: 0.5,
            data: userInfo,
          },
          {
            label: 'Company',
            backgroundColor: '#FFC24A',
            barPercentage: 0.5,
            data: companyInfo,
          },
        ],
      };
      return data;
    },
  },

  mounted() {
    this.renderChart(this.getData(this.chartValue, this.name), this.options);
    // console.log(this.chartValue.company);
    // console.log(this.num);
  },

  watch: {
    chartValue() {
      this.renderChart(this.getData(this.chartValue), this.options);
    },
    deep: true,
  },
};
</script>
