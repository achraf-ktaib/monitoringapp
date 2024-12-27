<template>
	<!-- Energy Initiatives Table -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{padding: 0,}">
		<template #title>
			<a-row type="flex" align="middle">
				<a-col :span="24" :md="12">
					<h5 class="font-semibold m-0">Initiatives Énergétiques</h5>
				</a-col>
				<a-col :span="24" :md="12" style="display: flex; align-items: center; justify-content: flex-end">
					<a-radio-group v-model="projectHeaderBtns" size="small">
						<a-radio-button value="all">TOUS</a-radio-button>
						<a-radio-button value="equipment">ÉQUIPEMENTS</a-radio-button>
						<a-radio-button value="process">PROCESSUS</a-radio-button>
					</a-radio-group>
				</a-col>
			</a-row>
		</template>
		<a-table :columns="columns" :data-source="data" :pagination="false">
			<template slot="name" slot-scope="text">
				<a>{{ text }}</a>
			</template>

			<template slot="type" slot-scope="type">
				<a-tag :color="getTypeColor(type)">{{ type }}</a-tag>
			</template>

			<template slot="consumption" slot-scope="consumption">
				<div class="consumption-data">
					<span class="current-value">{{ consumption.current }} kWh</span>
					<span class="variation" :class="consumption.trend">
						{{ consumption.variation }}%
						<a-icon :type="consumption.trend === 'decrease' ? 'arrow-down' : 'arrow-up'" />
					</span>
				</div>
			</template>

			<template slot="team" slot-scope="team">
				<a-space :size="-12" class="avatar-chips">
					<a-tooltip v-for="member in team" :key="member.id" :title="member.role">
						<a-avatar size="small" :src="member.avatar" />
					</a-tooltip>
				</a-space>
			</template>

			<template slot="status" slot-scope="status">
				<div class="status-container">
					<a-badge :status="getStatusType(status)" :text="status" />
				</div>
			</template>

			<template slot="efficiency" slot-scope="efficiency">
				<div class="efficiency-data">
					<div class="efficiency-header">
						<span>{{ efficiency.value }}%</span>
						<a-tag :color="getEfficiencyColor(efficiency.value)">
							{{ getEfficiencyLabel(efficiency.value) }}
						</a-tag>
					</div>
					<a-progress 
						:percent="efficiency.value" 
						:stroke-color="getEfficiencyColor(efficiency.value)"
						:show-info="false" 
						size="small" 
					/>
				</div>
			</template>

			<template slot="actions" slot-scope="row">
				<div class="action-buttons">
					<a-tooltip title="Voir détails">
						<a-button type="link" class="info-button">
							<a-icon type="eye" />
						</a-button>
					</a-tooltip>
					<a-tooltip title="Modifier">
						<a-button type="link" class="edit-button">
							<a-icon type="edit" />
						</a-button>
					</a-tooltip>
				</div>
			</template>
		</a-table>

		<div class="table-upload-btn">
			<a-button type="primary">
				<a-icon type="plus" />
				Nouvelle Initiative
			</a-button>
		</div>
	</a-card>
</template>

<script>
export default ({
	props: {
		data: {
			type: Array,
			default: () => [],
		},
		columns: {
			type: Array,
			default: () => [],
		},
	},
	data() {
		return {
			projectHeaderBtns: 'all',
		}
	},
	methods: {
		getTypeColor(type) {
			const colors = {
				'Équipement': '#1890ff',
				'Processus': '#722ed1',
				'Éclairage': '#52c41a',
				'HVAC': '#fa8c16'
			}
			return colors[type] || '#1890ff'
		},
		getStatusType(status) {
			const types = {
				'Optimal': 'success',
				'Normal': 'processing',
				'Attention': 'warning',
				'Critique': 'error'
			}
			return types[status] || 'default'
		},
		getEfficiencyColor(value) {
			if (value >= 90) return '#52c41a'
			if (value >= 70) return '#1890ff'
			if (value >= 50) return '#faad14'
			return '#f5222d'
		},
		getEfficiencyLabel(value) {
			if (value >= 90) return 'Excellent'
			if (value >= 70) return 'Bon'
			if (value >= 50) return 'Moyen'
			return 'Faible'
		}
	}
})
</script>

<style scoped>
.consumption-data {
	display: flex;
	flex-direction: column;
}

.current-value {
	font-weight: 600;
	color: #111827;
}

.variation {
	font-size: 12px;
	display: flex;
	align-items: center;
	gap: 4px;
}

.variation.decrease {
	color: #52c41a;
}

.variation.increase {
	color: #f5222d;
}

.efficiency-data {
	width: 200px;
}

.efficiency-header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 8px;
}

.status-container {
	display: flex;
	align-items: center;
}

.action-buttons {
	display: flex;
	gap: 8px;
}

:deep(.ant-table-thead > tr > th) {
	background: #fafafa;
	font-weight: 600;
}

:deep(.ant-progress-bg) {
	height: 6px !important;
}

:deep(.ant-tag) {
	border-radius: 4px;
}

.table-upload-btn {
	padding: 16px;
	background: #fafafa;
	border-top: 1px solid #f0f0f0;
}

:deep(.ant-btn-primary) {
	display: flex;
	align-items: center;
	gap: 8px;
}

.avatar-chips {
	display: flex;
	align-items: center;
}

:deep(.ant-avatar) {
	border: 2px solid white;
}

.info-button {
	color: #1890ff;
}

.edit-button {
	color: #722ed1;
}

:deep(.ant-badge-status-dot) {
	width: 8px;
	height: 8px;
}

:deep(.ant-badge-status-text) {
	margin-left: 8px;
}
</style>