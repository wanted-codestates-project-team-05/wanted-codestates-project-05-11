<script>
import { HorizontalBar } from 'vue-chartjs';

export default {
  extends: HorizontalBar,
  props: {
    chartData: Object,
    companyName: String,
  },
  mounted() {
    this.renderChart(this.getData(this.chartData), this.options, this.companyName);
  },
  watch: {
    companyName() {
      this.renderChart(this.getData(this.chartData), this.options, this.companyName);
    },
  },
  data() {
    return {
      options: {
        responsive: true,
        maintainAspectRatio: false,
        legend: {
          display: false,
        },
        tooltips: { enabled: false },
        hover: { mode: null },
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
    getData(chartData) {
      const makeGraphData = (data, maxScore) => {
        return Object.values(data).map((score) =>
          score >= maxScore / 2 || score === 0 ? score * -1 : maxScore - score
        );
      };
      const userGraphData = chartData.userData && makeGraphData(chartData.userData, chartData.maxScore);
      const bool = true;
      const companyGraphData = bool
        ? chartData.companyData && makeGraphData(chartData.companyData, chartData.maxScore)
        : [];
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
