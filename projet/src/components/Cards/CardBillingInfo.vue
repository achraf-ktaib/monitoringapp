<template>
	<!-- Energy Monitoring Information Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{paddingTop: 0, paddingBottom: '16px' }">
		<template #title>
			<h6 class="font-semibold m-0">Sites de Production - Informations Énergétiques</h6>
		</template>
		<a-row :gutter="[24, 24]">
			<a-col :span="24">
			<a-card :bordered="false" class="card-billing-info">
				<div class="col-info">
					<a-descriptions title="Site de Production Nord" :column="1">
						<a-descriptions-item label="Localisation">
							Zone Industrielle Nord
						</a-descriptions-item>
						<a-descriptions-item label="Consommation Mensuelle">
							45,000 kWh
						</a-descriptions-item>
						<a-descriptions-item label="ID Installation">
							SITE-NORD-001
						</a-descriptions-item>
					</a-descriptions>
				</div>
				<div class="col-action">
					<a-button type="primary" size="small">
						<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path class="fill-muted" d="M13.5858 3.58579C14.3668 2.80474 15.6332 2.80474 16.4142 3.58579C17.1953 4.36683 17.1953 5.63316 16.4142 6.41421L15.6213 7.20711L12.7929 4.37868L13.5858 3.58579Z" fill="#111827"/>
							<path class="fill-muted" d="M11.3787 5.79289L3 14.1716V17H5.82842L14.2071 8.62132L11.3787 5.79289Z" fill="#111827"/>
						</svg>
						<span>DÉTAILS</span>
					</a-button>
					<a-button type="link" size="small">
						<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path d="M10 12a2 2 0 100-4 2 2 0 000 4z" fill="#111827"/>
							<path d="M2 10C2 5.58172 5.58172 2 10 2V2C14.4183 2 18 5.58172 18 10V10C18 14.4183 14.4183 18 10 18V18C5.58172 18 2 14.4183 2 10V10Z" stroke="#111827" stroke-width="2"/>
						</svg>
						<span class="text-dark">MONITORING</span>
					</a-button>
				</div>
			</a-card>
			</a-col>
			<a-col :span="24">
			<a-card :bordered="false" class="card-billing-info">
				<div class="col-info">
					<a-descriptions title="Site de Production Sud" :column="1">
						<a-descriptions-item label="Localisation">
							Parc Industriel Sud
						</a-descriptions-item>
						<a-descriptions-item label="Consommation Mensuelle">
							38,500 kWh
						</a-descriptions-item>
						<a-descriptions-item label="ID Installation">
							SITE-SUD-002
						</a-descriptions-item>
					</a-descriptions>
				</div>
				<div class="col-action">
					<a-button type="primary" size="small">
						<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path class="fill-muted" d="M13.5858 3.58579C14.3668 2.80474 15.6332 2.80474 16.4142 3.58579C17.1953 4.36683 17.1953 5.63316 16.4142 6.41421L15.6213 7.20711L12.7929 4.37868L13.5858 3.58579Z" fill="#111827"/>
						</svg>
						<span>DÉTAILS</span>
					</a-button>
					<a-button type="link" size="small">
						<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path d="M10 12a2 2 0 100-4 2 2 0 000 4z" fill="#111827"/>
							<path d="M2 10C2 5.58172 5.58172 2 10 2V2C14.4183 2 18 5.58172 18 10V10C18 14.4183 14.4183 18 10 18V18C5.58172 18 2 14.4183 2 10V10Z" stroke="#111827" stroke-width="2"/>
						</svg>
						<span class="text-dark">MONITORING</span>
					</a-button>
				</div>
			</a-card>
			</a-col>
			<a-col :span="24">
			<a-card :bordered="false" class="card-billing-info">
				<div class="col-info">
					<a-descriptions title="Centre Logistique" :column="1">
						<a-descriptions-item label="Localisation">
							Zone Logistique Est
						</a-descriptions-item>
						<a-descriptions-item label="Consommation Mensuelle">
							25,800 kWh
						</a-descriptions-item>
						<a-descriptions-item label="ID Installation">
							LOG-EST-003
						</a-descriptions-item>
					</a-descriptions>
				</div>
				<div class="col-action">
					<a-button type="primary" size="small">
						<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path class="fill-muted" d="M13.5858 3.58579C14.3668 2.80474 15.6332 2.80474 16.4142 3.58579C17.1953 4.36683 17.1953 5.63316 16.4142 6.41421L15.6213 7.20711L12.7929 4.37868L13.5858 3.58579Z" fill="#111827"/>
						</svg>
						<span>DÉTAILS</span>
					</a-button>
					<a-button type="link" size="small">
						<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path d="M10 12a2 2 0 100-4 2 2 0 000 4z" fill="#111827"/>
							<path d="M2 10C2 5.58172 5.58172 2 10 2V2C14.4183 2 18 5.58172 18 10V10C18 14.4183 14.4183 18 10 18V18C5.58172 18 2 14.4183 2 10V10Z" stroke="#111827" stroke-width="2"/>
						</svg>
						<span class="text-dark">MONITORING</span>
					</a-button>
				</div>
			</a-card>
			</a-col>
		</a-row>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
		}
	},
})
</script>

<style scoped>
.card-billing-info {
	background: #f8fafc;
	border-radius: 8px;
	margin-bottom: 8px;
}

.col-info {
	padding: 16px;
}

.col-action {
	display: flex;
	gap: 8px;
	justify-content: flex-end;
	padding: 0 16px 16px;
}

:deep(.ant-descriptions-title) {
	color: #1890ff;
	font-weight: 600;
}

:deep(.ant-descriptions-item-label) {
	color: #666;
	font-weight: 500;
}

:deep(.ant-descriptions-item-content) {
	color: #111827;
	font-weight: 600;
}
</style>