<script>
import { Radar, mixins } from 'vue-chartjs';
const { reactiveProp } = mixins;

export default {
  extends: Radar,
  mixins: [reactiveProp],
  props: {
    chartdata: {
      type: Object,
      default: null,
    },
    options: {
      type: Object,
      default: null,
    },
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
  },
};
</script>
