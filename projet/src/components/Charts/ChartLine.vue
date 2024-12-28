<!-- Graphique de lignes pour les tensions (U1, U2, U3)-->
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
		type: "line",
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
			y: {
			  beginAtZero: true,
			  title: {
				display: true,
				text: "Tension (V)",
			  },
			},
			x: {
			  title: {
				display: true,
				text: "Temps",
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
  }
  </style>
  