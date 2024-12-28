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
    type: {
      type: String,
      default: "bar", // Permet d'utiliser différents types de graphiques si nécessaire
    },
    labels: {
      type: Object,
      default: () => ({
        x: "Phases",
        y: "Valeur",
      }),
    },
    stacked: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      chart: null,
    };
  },
  mounted() {
    const ctx = this.$refs.chart.getContext("2d");

    // Configuration des couleurs
    const colors = [
      "rgba(75, 192, 192, 0.8)",
      "rgba(255, 159, 64, 0.8)",
      "rgba(153, 102, 255, 0.8)",
      "rgba(255, 205, 86, 0.8)",
    ];

    this.chart = new Chart(ctx, {
      type: this.type,
      data: this.data,
      options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: true,
            position: "top",
          },
          tooltip: {
            enabled: true,
            mode: "index",
            intersect: false,
          },
          datalabels: {
            display: true, // Affiche les valeurs sur les barres
            color: "#000",
            anchor: "end",
            align: "top",
            formatter: (value) => value,
          },
        },
        animation: {
          duration: 1000,
          easing: "easeInOutQuart",
        },
        scales: {
          x: {
            stacked: this.stacked,
            title: {
              display: true,
              text: this.labels.x,
              color: "#333",
              font: {
                size: 14,
                weight: "bold",
              },
            },
            grid: {
              display: false,
            },
            ticks: {
              color: "#777",
            },
          },
          y: {
            stacked: this.stacked,
            beginAtZero: true,
            title: {
              display: true,
              text: this.labels.y,
              color: "#333",
              font: {
                size: 14,
                weight: "bold",
              },
            },
            ticks: {
              color: "#777",
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
  background: #f9f9f9;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
</style>
