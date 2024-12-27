<template>
	<!-- Energy Monitoring Settings Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{paddingTop: 0, paddingBottom: 0 }">
		<template #title>
			<h6 class="font-semibold m-0">Paramètres de Surveillance</h6>
		</template>
		<ul class="list settings-list">
			<li>
				<h6 class="list-header text-sm text-muted">ALERTES CRITIQUES</h6>
			</li>
			<li>
				<a-switch v-model="alertPeakConsumption" />
				<span>M'alerter en cas de pic de consommation</span>
			</li>
			<li>
				<a-switch v-model="alertAbnormalPattern"/>
				<span>M'alerter des comportements anormaux</span>
			</li>
			<li>
				<a-switch v-model="alertThreshold" />
				<span>M'alerter du dépassement des seuils définis</span>
			</li>
			<li>
				<h6 class="list-header text-sm text-muted m-0">RAPPORTS AUTOMATIQUES</h6>
			</li>
			<li>
				<a-switch v-model="dailyReport" />
				<span>Rapport quotidien de consommation</span>
			</li>
			<li>
				<a-switch v-model="weeklyAnalysis" />
				<span>Analyse hebdomadaire comparative</span>
			</li>
			<li>
				<a-switch v-model="monthlyEfficiency" />
				<span>Bilan mensuel d'efficacité énergétique</span>
			</li>
			<li>
				<h6 class="list-header text-sm text-muted m-0">MAINTENANCE</h6>
			</li>
			<li>
				<a-switch v-model="maintenanceAlerts" />
				<span>Alertes de maintenance préventive</span>
			</li>
			<li>
				<a-switch v-model="equipmentStatus" />
				<span>Statut des équipements en temps réel</span>
			</li>
		</ul>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
			// Alertes critiques
			alertPeakConsumption: true,
			alertAbnormalPattern: true,
			alertThreshold: true,

			// Rapports automatiques
			dailyReport: false,
			weeklyAnalysis: true,
			monthlyEfficiency: true,

			// Maintenance
			maintenanceAlerts: true,
			equipmentStatus: true
		}
	},
})
</script>

<style scoped>
.settings-list {
	list-style: none;
	padding: 24px;
	margin: 0;
}

.settings-list li {
	display: flex;
	align-items: center;
	padding: 12px 0;
	border-bottom: 1px solid #f0f0f0;
}

.settings-list li:last-child {
	border-bottom: none;
}

.list-header {
	color: #1890ff;
	font-size: 12px;
	font-weight: 600;
	margin: 8px 0;
	padding-top: 8px;
}

.settings-list span {
	margin-left: 16px;
	color: #111827;
	font-size: 14px;
}

:deep(.ant-switch-checked) {
	background-color: #52c41a;
}

:deep(.ant-switch) {
	min-width: 44px;
}

.text-muted {
	color: #666;
}

.text-sm {
	font-size: 12px;
}
</style>