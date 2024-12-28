<!--Graphique de barres empilées pour les puissances (P1, P2, P3)-->
<template>
    <div>
      <canvas ref="chart" :style="{ height: height + 'px' }"></canvas>
    </div>
  </template>
  
  <script>
  import { Chart, registerables } from "chart.js";
  Chart.register(...registerables);
  
  export default {
    props: {
      data: Object,
      height: {
        type: Number,
        default: 300,
      },
    },
    data() {
      return {
        chart: null,
      };
    },
    mounted() {
      const ctx = this.$refs.chart.getContext("2d");
      this.chart = new Chart(ctx, {
        type: "bar",
        data: this.data,
        options: {
          responsive: true,
          maintainAspectRatio: false,
          plugins: {
            legend: {
              display: true,
              position: "top",
            },
          },
          scales: {
            x: {
              stacked: true,
              title: {
                display: true,
                text: "Temps",
              },
            },
            y: {
              stacked: true,
              title: {
                display: true,
                text: "Puissance (kW)",
              },
            },
          },
        },
      });
    },
    beforeDestroy() {
      if (this.chart) {
        this.chart.destroy();
      }
    },
  };
  </script>
  
  <style scoped>
  canvas {
    background: #ffffff;
    border-radius: 8px;
    box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  }
  </style>
  