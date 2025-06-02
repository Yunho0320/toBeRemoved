<template>
  <div>
    <h2>Percentiles at Single X</h2>
    <div ref="plotContainer"></div>
  </div>
</template>

<script>
import Plotly from 'plotly.js';

export default {
  name: 'PercentileStrip',

  mounted() {
    const percentiles = [
      { label: 'P50', value: 993 },
      { label: 'P90', value: 2002 },
      { label: 'P99', value: 3500 },
      { label: 'P99.9', value: 4200 }
    ];

    const x = percentiles.map(() => 'latency'); // single x value repeated
    const y = percentiles.map(p => p.value);
    const text = percentiles.map(p => p.label);

    const trace = {
      x,
      y,
      type: 'scatter',
      mode: 'markers+text',
      text,
      textposition: 'right middle',
      marker: {
        size: 10,
        color: 'blue'
      },
      name: 'Percentiles'
    };

    const layout = {
      title: 'Latency Percentiles (Single X)',
      xaxis: {
        title: '',
        tickvals: ['latency'],
        showticklabels: false  // optional: hides x label since it's just one
      },
      yaxis: {
        title: 'Response Time (ms)'
      }
    };

    Plotly.newPlot(this.$refs.plotContainer, [trace], layout);
  }
};
</script>
