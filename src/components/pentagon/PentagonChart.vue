<script>
  import { Radar } from 'vue-chartjs'
  
  export default {
    extends: Radar,
    props: {
      chartdata: {
        type: Object,
        default: null,
      },
      options: {
        type: Object,
        default: null
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
    },
};
</script>
