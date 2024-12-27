<template>
	<!-- Production Sites Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{paddingTop: 0,}">
		<template #title>
			<a-row type="flex" align="middle">
				<a-col :span="24" :md="12">
					<h6 class="font-semibold m-0">Sites de Production</h6>
				</a-col>
				<a-col :span="24" :md="12" style="display: flex; align-items: center; justify-content: flex-end">
					<a-button type="primary">
						AJOUTER UN SITE
					</a-button>
				</a-col>
			</a-row>
		</template>
		<a-row :gutter="[24, 24]">
			<a-col :span="24" :md="12">
				<a-card class="site-card">
					<div class="site-header">
						<div class="site-icon manufacturing">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 21V5a2 2 0 00-2-2H7a2 2 0 00-2 2v16m14 0h2m-2 0h-5m-9 0H3m2 0h5M9 7h1m-1 4h1m4-4h1m-1 4h1m-5 10v-5a1 1 0 011-1h2a1 1 0 011 1v5m-4 0h4"/>
							</svg>
						</div>
						<h6 class="site-name">Site Nord - Production</h6>
					</div>
					<div class="site-stats">
						<div class="stat-item">
							<span class="label">Consommation</span>
							<span class="value">45,000 kWh/mois</span>
						</div>
						<div class="stat-item">
							<span class="label">Efficacité</span>
							<span class="value success">92%</span>
						</div>
					</div>
					<a-button type="primary" ghost class="action-button">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path d="M13.5858 3.58579C14.3668 2.80474 15.6332 2.80474 16.4142 3.58579C17.1953 4.36683 17.1953 5.63316 16.4142 6.41421L15.6213 7.20711L12.7929 4.37868L13.5858 3.58579Z" fill="currentColor"/>
							<path d="M11.3787 5.79289L3 14.1716V17H5.82842L14.2071 8.62132L11.3787 5.79289Z" fill="currentColor"/>
						</svg>
						<span>CONFIGURER</span>
					</a-button>
				</a-card>
			</a-col>
			<a-col :span="24" :md="12">
				<a-card class="site-card">
					<div class="site-header">
						<div class="site-icon logistics">
							<svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor">
								<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 8h14M5 8a2 2 0 110-4h14a2 2 0 110 4M5 8v10a2 2 0 002 2h10a2 2 0 002-2V8m-9 4h4"/>
							</svg>
						</div>
						<h6 class="site-name">Site Sud - Logistique</h6>
					</div>
					<div class="site-stats">
						<div class="stat-item">
							<span class="label">Consommation</span>
							<span class="value">28,500 kWh/mois</span>
						</div>
						<div class="stat-item">
							<span class="label">Efficacité</span>
							<span class="value warning">85%</span>
						</div>
					</div>
					<a-button type="primary" ghost class="action-button">
						<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path d="M13.5858 3.58579C14.3668 2.80474 15.6332 2.80474 16.4142 3.58579C17.1953 4.36683 17.1953 5.63316 16.4142 6.41421L15.6213 7.20711L12.7929 4.37868L13.5858 3.58579Z" fill="currentColor"/>
							<path d="M11.3787 5.79289L3 14.1716V17H5.82842L14.2071 8.62132L11.3787 5.79289Z" fill="currentColor"/>
						</svg>
						<span>CONFIGURER</span>
					</a-button>
				</a-card>
			</a-col>
		</a-row>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
			sites: [
				{
					name: "Site Nord - Production",
					type: "manufacturing",
					consumption: "45,000",
					efficiency: 92,
					status: "success"
				},
				{
					name: "Site Sud - Logistique",
					type: "logistics",
					consumption: "28,500",
					efficiency: 85,
					status: "warning"
				}
			]
		}
	},
})
</script>

<style scoped>
.site-card {
	background: #f8fafc;
	border-radius: 12px;
}

.site-header {
	display: flex;
	align-items: center;
	gap: 16px;
	margin-bottom: 20px;
}

.site-icon {
	width: 48px;
	height: 48px;
	border-radius: 12px;
	display: flex;
	align-items: center;
	justify-content: center;
	color: white;
}

.site-icon.manufacturing {
	background: linear-gradient(135deg, #1890ff 0%, #096dd9 100%);
}

.site-icon.logistics {
	background: linear-gradient(135deg, #722ed1 0%, #531dab 100%);
}

.site-name {
	font-size: 16px;
	font-weight: 600;
	margin: 0;
	color: #111827;
}

.site-stats {
	display: grid;
	grid-template-columns: 1fr 1fr;
	gap: 16px;
	margin-bottom: 20px;
}

.stat-item {
	display: flex;
	flex-direction: column;
	gap: 4px;
}

.stat-item .label {
	font-size: 12px;
	color: #666;
}

.stat-item .value {
	font-size: 16px;
	font-weight: 600;
	color: #111827;
}

.value.success {
	color: #52c41a;
}

.value.warning {
	color: #faad14;
}

.action-button {
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	gap: 8px;
}

:deep(.ant-card-body) {
	padding: 20px;
}
</style>