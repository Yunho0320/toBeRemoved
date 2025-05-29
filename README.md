# toBeRemoved

<template>
  <div>
    <h2>Latency Percentile Scar Plot</h2>
    <ScatterChart :chart-data="chartData" :chart-options="chartOptions" />
  </div>
</template>

<script>
import {
  Chart as ChartJS,
  ScatterController,
  PointElement,
  LinearScale,
  CategoryScale,
  Tooltip,
  Legend,
} from 'chart.js'
import { defineComponent } from 'vue'
import { Scatter } from 'vue-chartjs'

ChartJS.register(
    ScatterController,
    PointElement,
    LinearScale,
    CategoryScale,
    Tooltip,
    Legend
)

export default defineComponent({
  name: 'HelloWorld',
  components: {
    ScatterChart: Scatter
  },
  data() {
    return {
      chartData: {
        datasets: [
          // 🔵 Metric A (blue)
          {
            label: 'Metric A - min',
            data: [
              { x: '09:06', y: 5 },
              { x: '09:07', y: 6 },
              { x: '09:08', y: 5 }
            ],
            pointBackgroundColor: 'blue',
            pointRadius: 5,
            showLine: false
          },
          {
            label: 'Metric A - p50',
            data: [
              { x: '09:06', y: 100 },
              { x: '09:07', y: 110 },
              { x: '09:08', y: 105 }
            ],
            pointBackgroundColor: 'blue',
            pointRadius: 5,
            showLine: false
          },
          {
            label: 'Metric A - p95',
            data: [
              { x: '09:06', y: 200 },
              { x: '09:07', y: 212 },
              { x: '09:08', y: 220 }
            ],
            pointBackgroundColor: 'blue',
            pointRadius: 5,
            showLine: false
          },

          // 🟢 Metric B (green)
          {
            label: 'Metric B - min',
            data: [
              { x: '09:06', y: 8 },
              { x: '09:07', y: 9 },
              { x: '09:08', y: 8 }
            ],
            pointBackgroundColor: 'green',
            pointRadius: 5,
            showLine: false
          },
          {
            label: 'Metric B - p50',
            data: [
              { x: '09:06', y: 120 },
              { x: '09:07', y: 125 },
              { x: '09:08', y: 118 }
            ],
            pointBackgroundColor: 'green',
            pointRadius: 5,
            showLine: false
          },
          {
            label: 'Metric B - p95',
            data: [
              { x: '09:06', y: 240 },
              { x: '09:07', y: 260 },
              { x: '09:08', y: 275 }
            ],
            pointBackgroundColor: 'green',
            pointRadius: 5,
            showLine: false
          }
        ]
      }
    }
  }
})
</script>
