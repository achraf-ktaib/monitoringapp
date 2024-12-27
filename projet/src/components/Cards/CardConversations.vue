<template>
	<!-- Energy Alerts Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{paddingTop: 0, paddingBottom: '16px' }">
		<template #title>
			<h6 class="font-semibold m-0">Alertes & Notifications</h6>
		</template>
		<a-list
			class="alerts-list"
			item-layout="horizontal"
			:split="false"
			:data-source="data"
		>
			<a-list-item slot="renderItem" slot-scope="item">
				<a-button 
					slot="actions" 
					type="primary" 
					:class="item.priority"
					size="small"
				>
					VÉRIFIER
				</a-button>
				<a-list-item-meta
					:title="item.title"
					:description="item.timestamp"
				>
					<a-avatar
						slot="avatar"
						:size="48"
						shape="square"
						:class="['alert-icon', item.type]"
					>
						<template v-if="item.type === 'warning'">⚠️</template>
						<template v-if="item.type === 'critical'">🔴</template>
						<template v-if="item.type === 'info'">ℹ️</template>
					</a-avatar>
				</a-list-item-meta>
			</a-list-item>
		</a-list>
	</a-card>
</template>

<script>
export default ({
	props: {
		data: {
			type: Array,
			default: () => [
				{
					title: "Pic de consommation détecté - Site Nord",
					timestamp: "Il y a 5 minutes",
					type: "warning",
					priority: "medium"
				},
				{
					title: "Maintenance préventive requise - Unité 3",
					timestamp: "Il y a 30 minutes",
					type: "info",
					priority: "low"
				},
				{
					title: "Dépassement seuil critique - Site Sud",
					timestamp: "Il y a 1 heure",
					type: "critical",
					priority: "high"
				},
				{
					title: "Objectif mensuel atteint - Centre Logistique",
					timestamp: "Il y a 2 heures",
					type: "info",
					priority: "low"
				}
			]
		},
	},
	data() {
		return {}
	},
})
</script>

<style scoped>
.alerts-list {
	padding: 0 10px;
}

.alert-icon {
	display: flex;
	align-items: center;
	justify-content: center;
}

.alert-icon.warning {
	background-color: #fff3e0;
}

.alert-icon.critical {
	background-color: #ffebee;
}

.alert-icon.info {
	background-color: #e3f2fd;
}

:deep(.ant-list-item-meta-title) {
	font-size: 14px;
	font-weight: 600;
}

:deep(.ant-list-item-meta-description) {
	font-size: 12px;
	color: #666;
}

.high {
	background-color: #f44336;
	color: white;
}

.medium {
	background-color: #ff9800;
	color: white;
}

.low {
	background-color: #2196f3;
	color: white;
}

:deep(.ant-list-item) {
	padding: 12px 0;
	border-bottom: 1px solid #f0f0f0;
}

:deep(.ant-list-item:last-child) {
	border-bottom: none;
}
</style>