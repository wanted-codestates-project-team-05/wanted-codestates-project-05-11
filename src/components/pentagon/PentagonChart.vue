<script>
import { Radar } from 'vue-chartjs';
export default {
  name: 'PentagonChart',
  extends: Radar,
  mounted() {
    this.renderChart(
      {
        labels: [
          '적극적인 Aggressive',
          '자신있는 Confident',
          '책임있는 Responsible',
          '개인주의 Indivisual',
          '수평적인 Horizontal',
        ],
        datasets: [
          {
            label: '모두',
            backgroundColor: 'green',
            // borderColor: 'rgba(179,181,198,1)',
            // pointBackgroundColor: 'rgba(179,181,198,1)',
            // pointBorderColor: '#fff',
            // pointHoverBackgroundColor: '#fff',
            // pointHoverBorderColor: 'rgba(179,181,198,1)',
            // borderJoinStyle: 'round',
            // data: [8, 8, 7, 8, 4],
            // onclick: () => {
            //   console.log(1);
            // },
          },
          {
            label: '본인',
            backgroundColor: 'rgba(110, 60, 249, 0.32)',
            borderColor: 'rgba(110, 60, 249, 1)',
            pointBackgroundColor: 'rgba(110, 60, 249, 1)',
            pointBorderColor: 'rgba(110, 60, 249, 1)',
            pointHoverBackgroundColor: '#fff',
            pointHoverBorderColor: 'rgba(110, 60, 249, 1)',
            pointBorderWidth: 0,
            pointStyle: 'dash',
            hitRadius: 0,
            data: [6, 7, 4, 5, 7],
          },
          {
            label: '회사',
            backgroundColor: 'rgba(255, 193, 74, 0.32)',
            borderColor: 'rgba(255, 211, 53, 1)',
            pointBackgroundColor: 'rgba(255, 211, 53, 1)',
            pointBorderColor: 'rgba(255, 211, 53, 1)',
            pointHoverBackgroundColor: '#fff',
            pointHoverBorderColor: 'rgba(255, 211, 53, 1)',
            borderJoinStyle: 'round',
            pointStyle: 'dash',
            data: [8, 8, 7, 8, 4],
          },
          // {
          //   label: '회사',
          //   backgroundColor: 'rgba(255, 193, 74, 0.32)',
          //   borderColor: 'rgba(0, 0, 0, 0)',
          //   borderWidth: 0,
          //   pointBackgroundColor: 'red',
          //   pointBorderColor: 'rgba(255, 211, 53, 1)',
          //   pointHoverBackgroundColor: '#fff',
          //   pointHoverBorderColor: 'rgba(255, 211, 53, 1)',
          //   borderJoinStyle: 'round',
          //   pointStyle: 'dash',
          //   data: [0, 10, 0, 0, 0],
          // },
        ],
      },
      {
        responsive: true,
        maintainAspectRatio: false,
        scale: {
          ticks: {
            display: false,
            suggestedMin: 0,
            suggestedMax: 10,
            stepSize: 2,
            callback: function (tick, index) {
              return index === 3 ? { borderDash: [2] } : null;
            },
          },
          gridLines: {
            // callbacks: {
            //   borderDash: function (context) {
            //     return context.index === 3 ? [5, 5] : [];
            //   },
            // },
            borderDash: [3, 2],
            // borderDash[gridLines.ticks.length]: [5],
            // zeroLineWidth: 16,
            // zeroLineColor: 'rgba(255, 211, 53, 1)',
          },
        },
        legend: {
          position: 'bottom',
        },
      }
    );
  },
};
</script>
