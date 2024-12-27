<template>
	<a-card :bordered="false" class="dashboard-bar-line header-solid">
		<template #title>
			<h6>Évolution de la Consommation</h6>			
			<p>par rapport à l'année précédente <span :class="yearlyVariation < 0 ? 'text-success' : 'text-danger'">{{ yearlyVariation }}%</span></p>	
		</template>
		<template #extra>
			<a-badge color="#1890FF" class="badge-dot-primary" text="Consommation Réelle" />
			<a-badge color="#52C41A" class="badge-dot-secondary" text="Objectif" />
		</template>
		<chart-line :height="310" :data="lineChartData"></chart-line>
		<div class="chart-info">
			<div class="info-item">
				<span class="label">Pic de consommation</span>
				<span class="value">58,500 kWh</span>
				<span class="date">Août 2023</span>
			</div>
			<div class="info-item">
				<span class="label">Moyenne mensuelle</span>
				<span class="value">42,300 kWh</span>
				<span class="date">2023</span>
			</div>
		</div>
	</a-card>
</template>

<script>
import ChartLine from '../Charts/ChartLine';

export default ({
	components: {
		ChartLine,
	},
	data() {
		return {
			yearlyVariation: -12.5,
			// Données pour le graphique linéaire
			lineChartData: {
				labels: ["Jan", "Fév", "Mar", "Avr", "Mai", "Jun", "Jul", "Aoû", "Sep", "Oct", "Nov", "Déc"],
				datasets: [{
					label: "Consommation Réelle",
					tension: 0.4,
					borderWidth: 3,
					pointRadius: 4,
					pointBackgroundColor: "#1890FF",
					borderColor: "#1890FF",
					backgroundColor: "rgba(24, 144, 255, 0.1)",
					fill: true,
					data: [42000, 38000, 45000, 40000, 48000, 51000, 55000, 58500, 52000, 49000, 45000, 43000],
					maxBarThickness: 6
				},
				{
					label: "Objectif",
					tension: 0.4,
					borderWidth: 3,
					pointRadius: 0,
					borderColor: "#52C41A",
					borderDash: [5, 5],
					data: [45000, 45000, 45000, 45000, 45000, 45000, 45000, 45000, 45000, 45000, 45000, 45000],
					maxBarThickness: 6
				}],
			},
		}
	},
})
</script>

<style scoped>
.dashboard-bar-line {
	background: white;
	border-radius: 12px;
}

.dashboard-bar-line :deep(.ant-card-head) {
	padding: 16px 24px;
}

.dashboard-bar-line :deep(.ant-card-head-title) h6 {
	font-size: 16px;
	font-weight: 600;
	margin-bottom: 4px;
}

.dashboard-bar-line :deep(.ant-card-head-title) p {
	font-size: 14px;
	color: #666;
	margin: 0;
}

.text-success {
	color: #52C41A;
}

.text-danger {
	color: #F5222D;
}

.badge-dot-primary,
.badge-dot-secondary {
	margin-left: 16px;
}

.chart-info {
	display: flex;
	justify-content: space-around;
	margin-top: 24px;
	padding: 0 24px;
}

.info-item {
	display: flex;
	flex-direction: column;
	align-items: center;
	text-align: center;
}

.info-item .label {
	font-size: 12px;
	color: #666;
	margin-bottom: 4px;
}

.info-item .value {
	font-size: 18px;
	font-weight: 600;
	color: #111827;
	margin-bottom: 2px;
}

.info-item .date {
	font-size: 12px;
	color: #999;
}

:deep(.ant-badge-status-text) {
	margin-left: 4px;
	font-size: 13px;
}
</style>