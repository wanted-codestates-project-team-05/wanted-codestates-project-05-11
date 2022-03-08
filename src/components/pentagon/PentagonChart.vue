<script>
import { Radar } from "vue-chartjs";
export default {
  extends: Radar,
  methods: {
    drawRadar() {
      const chartData = {
        labels: [
          ["적극적인", "Aggressive"],
          ["자신있는", "Confident"],
          ["책임있는", "Responsible"],
          ["개인주의", "Indivisual"],
          ["수평적인", "Horizontal"],
        ],
        datasets: [
          {
            backgroundColor: "rgba(110, 60, 249, 0.32)",
            borderColor: "#6E3CF9",
            borderWidth: 2,
            borderRadius: 1,
            pointBackgroundColor: "rgba(255,99,132,1)",
            pointRadius: 0,
            pointHitRadius: 0,
            order: 2,
            data:[8, 10, 10, 3, 6],
          },
          {
            backgroundColor: "rgba(255, 193, 74, 0.32)",
            borderColor: "#FFD335",
            borderWidth: 2,
            borderRadius: 1,
            pointRadius: 0,
            pointHitRadius: 0,
            order: 1,
            data:[7, 8, 6, 8, 4],
          },
          {
            backgroundColor: "rgba(244, 244, 244, 0.32)",
            borderColor: "#B2B2B2",
            borderWidth: 1,
            pointBackgroundColor: [
              "rgba(237, 168, 154, 0.7)",
              "rgba(182, 197, 248, 0.7)",
              "rgba(164, 214, 227, 0.7)",
              "rgba(238, 184, 207, 0.7)",
              "rgba(183, 220, 171, 0.7)",
            ],
            pointBorderColor: [
              "#EDA89A",
              "#B6C5F8",
              "#A4D6E3",
              "#EEB8CF",
              "#B7DCAB",
            ],
            pointRadius: 18,
            data: [10, 10, 10, 10, 10],
          },
        ],
      };
      return chartData;
    },
  },
  data() {
    return {
      options: {
        enabled: true,
        responsive: true,
        tooltips: {
            enabled: false
        },
        maintainAspectRatio: false,
        legend: {
          display: false,
        },
        hover : false,
        layout: {
          padding: 10
        },
        elements: {
          point: {
            hoverRadius: '18',
          },
        },
        scale: {
          pointLabels: {
            fontFamily: "Noto Sans",
            fontStyle: "bold",
            fontColor: "black",
            fontSize: 12,
            lineHeight: 1.5,
          },
          ticks: {
            max: 10,
            min: 0,
            stepSize: 2.5,
            display: false,
          },
          gridLines: {
            borderDash: [5, 5]
          }
        },
      },
    };
  },
  mounted() {
    this.renderChart(this.drawRadar(), this.options);
  }
};
</script>