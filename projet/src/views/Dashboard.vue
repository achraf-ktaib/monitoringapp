<template>
	<div>
	  <!-- Counter Widgets -->
	  <a-row :gutter="24">
		<a-col
		  :span="24"
		  :lg="12"
		  :xl="6"
		  class="mb-24"
		  v-for="(stat, index) in stats"
		  :key="index"
		>
		  <!-- Widget Card for Energy KPI -->
		  <WidgetCounter
			:title="stat.title"
			:value="stat.value"
			:suffix="stat.suffix"
			:icon="stat.icon"
		  />
		  <!-- / Widget Card -->
		</a-col>
	  </a-row>
	  <!-- / Counter Widgets -->
  
	  <!-- Charts -->
	  <a-row :gutter="24" type="flex" align="stretch">
		<a-col :span="24" :lg="12" class="mb-24">
		  <!-- Voltage Chart -->
		  <CardBarChart :title="'Tensions des phases (U1, U2, U3)'" />
		  <!-- / Voltage Chart -->
		</a-col>
		<a-col :span="24" :lg="12" class="mb-24">
		  <!-- Current Chart -->
		  <CardLineChart :title="'Courants des phases (I1, I2, I3)'" />
		  <!-- / Current Chart -->
		</a-col>
	  </a-row>
  
	  <!-- New Charts Side by Side -->
	  <a-row :gutter="24" type="flex" align="stretch">
		<a-col :span="24" :lg="12" class="mb-24">
		  <harmonics-chart :data="harmonicsData" :height="400" />
		</a-col>
		<a-col :span="24" :lg="12" class="mb-24">
		  <stacked-bar-chart :data="stackedData" :height="400" />
		</a-col>
	  </a-row>
  
	  <!-- Table & Alerts -->
	  <a-row :gutter="24" type="flex" align="stretch">
		<!-- Table for Equipment -->
		<a-col :span="24" :lg="16" class="mb-24">
		  <CardProjectTable :data="tableData" :columns="tableColumns" />
		</a-col>
  
		<!-- Alerts Timeline -->
		<a-col :span="24" :lg="8" class="mb-24">
		  <CardOrderHistory :title="'Alertes et Dysfonctionnements'" />
		</a-col>
	  </a-row>
	</div>
  </template>
  
  <script>
  import CardBarChart from "../components/Cards/CardBarChart";
  import CardLineChart from "../components/Cards/CardLineChart";
  import WidgetCounter from "../components/Widgets/WidgetCounter";
  import CardProjectTable from "../components/Cards/CardProjectTable";
  import CardOrderHistory from "../components/Cards/CardOrderHistory";
  import HarmonicsChart from "../components/Charts/HarmonicsChart";
  import StackedBarChart from "../components/Charts/StackedBarChart";
  
  const stats = [
	{
	  title: "Tension Moyenne",
	  value: "220V",
	  icon: "<svg>...</svg>",
	},
	{
	  title: "Courant Moyen",
	  value: "10A",
	  icon: "<svg>...</svg>",
	},
	{
	  title: "Puissance Totale",
	  value: "5kW",
	  icon: "<svg>...</svg>",
	},
	{
	  title: "Facteur de Puissance",
	  value: "0.95",
	  icon: "<svg>...</svg>",
	},
  ];
  
  const tableColumns = [
	{
	  title: "Équipement",
	  dataIndex: "equipment",
	  key: "equipment",
	},
	{
	  title: "Consommation (kWh)",
	  dataIndex: "consumption",
	  key: "consumption",
	},
	{
	  title: "Statut",
	  dataIndex: "status",
	  key: "status",
	},
  ];
  
  const tableData = [
	{
	  key: "1",
	  equipment: "Pompe Hydraulique",
	  consumption: "50",
	  status: "Normal",
	},
	{
	  key: "2",
	  equipment: "Machine CNC",
	  consumption: "120",
	  status: "Élevée",
	},
	{
	  key: "3",
	  equipment: "Système de Climatisation",
	  consumption: "30",
	  status: "Normal",
	},
  ];
  
  export default {
	components: {
	  CardBarChart,
	  CardLineChart,
	  WidgetCounter,
	  CardProjectTable,
	  CardOrderHistory,
	  HarmonicsChart,
	  StackedBarChart,
	},
	data() {
	  return {
		stats,
		tableData,
		tableColumns,
		harmonicsData: {
		  labels: ['Phase 1', 'Phase 2', 'Phase 3'],
		  datasets: [
			{
			  label: "Harmoniques",
			  backgroundColor: "#36A2EB",
			  data: [30, 50, 70],
			},
		  ],
		},
		stackedData: {
		  labels: ['P1', 'P2', 'P3'],
		  datasets: [
			{
			  label: "Puissance",
			  backgroundColor: "#FF6384",
			  data: [300, 500, 400],
			},
			{
			  label: "Consommation",
			  backgroundColor: "#36A2EB",
			  data: [200, 300, 250],
			},
		  ],
		},
	  };
	},
  };
  </script>
  
  <style lang="scss">
  </style>
  