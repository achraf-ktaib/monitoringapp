<template>
	<!-- Energy Projects Table Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{padding: 0,}">
		<template #title>
			<a-row type="flex" align="middle">
				<a-col :span="24" :md="12">
					<h6>Projets d'Optimisation</h6>			
					<p>ce mois-ci <span class="text-success">-15% de consommation</span></p>	
				</a-col>
				<a-col :span="24" :md="12" style="display: flex; align-items: center; justify-content: flex-end">
					<a-radio-group v-model="projectFilter" size="small">
						<a-radio-button value="all">TOUS</a-radio-button>
						<a-radio-button value="active">EN COURS</a-radio-button>
						<a-radio-button value="completed">TERMINÉS</a-radio-button>
					</a-radio-group>
				</a-col>
			</a-row>
		</template>
		<a-table :columns="columns" :data-source="data" :pagination="false">
			<template slot="site" slot-scope="site">
				<h6 class="m-0">
					<a-icon :type="site.icon" class="site-icon" :style="{ color: site.iconColor }" />
					{{ site.name }}
				</h6>
			</template>

			<template slot="savings" slot-scope="savings">
				<div class="savings-cell">
					<span class="savings-value">{{ savings.energy }} kWh/an</span>
					<span class="savings-co2">{{ savings.co2 }} tCO2</span>
				</div>
			</template>

			<template slot="budget" slot-scope="budget">
				<div class="budget-cell">
					<span class="budget-value">{{ budget.value }}k€</span>
					<span class="budget-roi">ROI: {{ budget.roi }} ans</span>
				</div>
			</template>

			<template slot="status" slot-scope="status">
				<a-tag :color="getStatusColor(status)">{{ status }}</a-tag>
			</template>

			<template slot="team" slot-scope="team">
				<a-space :size="-12" class="avatar-chips">
					<a-tooltip v-for="member in team" :key="member.id" :title="member.role">
						<a-avatar size="small" :src="member.avatar" />
					</a-tooltip>
				</a-space>
			</template>

			<template slot="progress" slot-scope="progress">
				<div class="progress-cell">
					<div class="progress-header">
						<span class="progress-phase">{{ progress.phase }}</span>
						<span class="progress-value">{{ progress.value }}%</span>
					</div>
					<a-progress 
						:percent="progress.value" 
						:status="getProgressStatus(progress.value)"
						:show-info="false" 
						size="small"
					/>
				</div>
			</template>
		</a-table>

		<div class="table-upload-btn">
			<a-button type="primary">
				<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
					<path d="M10 3a1 1 0 011 1v5h5a1 1 0 110 2h-5v5a1 1 0 11-2 0v-5H4a1 1 0 110-2h5V4a1 1 0 011-1z" fill="currentColor"/>
				</svg>
				Nouveau Projet d'Optimisation
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
			projectFilter: 'all'
		}
	},
	methods: {
		getStatusColor(status) {
			const colors = {
				'En cours': '#1890ff',
				'Terminé': '#52c41a',
				'Planifié': '#722ed1',
				'En pause': '#faad14'
			}
			return colors[status] || '#1890ff'
		},
		getProgressStatus(value) {
			if (value >= 100) return 'success'
			if (value >= 70) return 'active'
			return 'normal'
		}
	}
})
</script>

<style scoped>
.site-icon {
	font-size: 18px;
	margin-right: 8px;
}

.savings-cell {
	display: flex;
	flex-direction: column;
}

.savings-value {
	font-weight: 600;
	color: #111827;
}

.savings-co2 {
	font-size: 12px;
	color: #52c41a;
}

.budget-cell {
	display: flex;
	flex-direction: column;
}

.budget-value {
	font-weight: 600;
	color: #111827;
}

.budget-roi {
	font-size: 12px;
	color: #666;
}

.progress-cell {
	width: 200px;
}

.progress-header {
	display: flex;
	justify-content: space-between;
	margin-bottom: 4px;
}

.progress-phase {
	font-size: 12px;
	color: #1890ff;
}

.progress-value {
	font-size: 12px;
	color: #666;
}

:deep(.ant-table-thead > tr > th) {
	background: #fafafa;
	font-weight: 600;
}

:deep(.ant-progress-bg) {
	height: 6px !important;
}

.text-success {
	color: #52c41a;
}

.table-upload-btn {
	padding: 16px;
	background: #fafafa;
	border-top: 1px solid #f0f0f0;
}

:deep(.ant-btn-primary) {
	display: flex;
	align-items: center;
	justify-content: center;
	gap: 8px;
}

:deep(.ant-tag) {
	min-width: 80px;
	text-align: center;
}

.avatar-chips {
	display: flex;
	align-items: center;
}

:deep(.ant-avatar) {
	border: 2px solid white;
}
</style>