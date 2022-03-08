<script>
import { Radar, mixins } from 'vue-chartjs';
import companyData from '../../assets/company.json';
const { reactiveProp } = mixins;

const data = companyData.KAKAO;

const dataChart = [];
for (let key in data) {
  dataChart.push(data[key]);
}
export default {
  extends: Radar,
  mixins: [reactiveProp],
  // data: () => {
  //   company: company;
  // },
  props: {
    chartdata: {
      type: Object,
      default: null,
    },
    options: {
      type: Object,
      default: null,
    },
    company: String,
  },
  watch: {
    chartdata() {
      this.render();
    },
  },
  methods: {
    render() {
      this.renderChart(this.chartdata, this.options);
    },
  },
  mounted() {
    this.render();
    console.log(data);
    console.log(this.company);
    console.log(dataChart);
  },
};
</script>
