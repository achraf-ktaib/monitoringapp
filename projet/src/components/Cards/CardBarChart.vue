<template>
	<!-- Active Users Card (Adjusted for Energy Consumption Tracking) -->
	<a-card :bordered="false" class="dashboard-bar-chart">
	  <chart-bar :height="220" :data="barChartData"></chart-bar>
	  <div class="card-title">
		<h6>Billing Information Overview</h6>
		<p>Compared to last month <span class="text-success">+15%</span></p>
	  </div>
	  <div class="card-content">
		<p>This chart displays the total energy consumption across various departments in your organization.</p>
	  </div>
	  <a-row class="card-footer" type="flex" justify="center" align="top">
		<a-col :span="6">
		  <h4>15kWh</h4>
		  <span>Usine1</span>
		</a-col>
		<a-col :span="6">
		  <h4>10kWh</h4>
		  <span>Usine2</span>
		</a-col>
		<a-col :span="6">
		  <h4>8kWh</h4>
		  <span>Usine3</span>
		</a-col>
		<a-col :span="6">
		  <h4>5kWh</h4>
		  <span>Bureaux</span>
		</a-col>
	  </a-row>
	</a-card>
	<!-- / Active Users Card -->
  </template>
  
  <script>
  // Bar chart for "Energy Consumption Overview" card.
  import ChartBar from '../Charts/ChartBar';
  
  export default {
	components: {
	  ChartBar,
	},
	data() {
	  return {
		// Data for bar chart.
		barChartData: {
		  labels: ['Usine1', 'Usine 2', 'Usine3', 'Bureaux'],
		  datasets: [
			{
			  label: 'Energy Consumption (kWh)',
			  backgroundColor: '#FFFFFF',
			  borderWidth: 0,
			  borderRadius: 6,
			  data: [15000, 10000, 8000, 5000],
			  maxBarThickness: 20,
			},
		  ],
		},
	  };
	},
  };
  </script>
  
  <style scoped>
  .dashboard-bar-chart {
	padding: 16px;
	background-color: #f5f5f5;
  }
  
  .card-title {
	text-align: center;
	margin-top: 16px;
  }
  
  .card-footer {
	margin-top: 16px;
	text-align: center;
  }
  .card-footer h4 {
	font-weight: 600;
	margin-bottom: 4px;
  }
  
  .card-footer span {
	color: #888;
	font-size: 12px;
  }
  </style>
  