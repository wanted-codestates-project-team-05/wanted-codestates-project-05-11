<script>
import { HorizontalBar, mixins } from 'vue-chartjs';

export default {
  extends: HorizontalBar,
  mixins: [mixins.reactiveProp],
  props: {
    userData: Object,
    companyData: Object,
    chartData: Object,
    maxScore: Number,
  },
  mounted() {
    this.renderChart(this.getData(this.userData, this.companyData, this.maxScore), this.options, this.chartData);
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
                display: true,
                drawBorder: false,
                lineWidth: 1,
                color: 'darkGrey',
                offsetGridLines: false,
              },
              ticks: {
                display: false,
                fontSize: 20,
                beginAtZero: true,
              },
            },
          ],
          xAxes: [
            {
              gridLines: {
                display: true,
                lineWidth: 0,
                drawBorder: false,
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
    getData(userData, companyData, maxScore) {
      const makeGraphData = (data, maxScore) => {
        return Object.values(data).map((score) =>
          score >= maxScore / 2 || score === 0 ? score * -1 : maxScore - score
        );
      };
      const userGraphData = userData && makeGraphData(userData, maxScore);
      const companyGraphData = companyData && makeGraphData(companyData, maxScore);
      const data = {
        labels: ['type1', 'type2', 'type3', 'type4', 'type5'],
        datasets: [
          {
            label: 'User',
            backgroundColor: '#6E3CF9',
            barPercentage: 0.5,
            data: userGraphData,
          },
          {
            label: 'Company',
            backgroundColor: '#FFC24A',
            barPercentage: 0.5,
            data: companyGraphData,
          },
        ],
      };
      return data;
    },
  },
};
</script>
