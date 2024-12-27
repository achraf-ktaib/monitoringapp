<template>
	<!-- Site Information Card -->
	<a-card :bordered="false" class="header-solid h-full card-site-information" :bodyStyle="{paddingTop: 0, paddingBottom: '16px' }" :headStyle="{paddingRight: 0,}">
		<template #title>
			<h6 class="font-semibold m-0">Information du Site</h6>
		</template>
		<a-button type="link" slot="extra">
			<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<path class="fill-muted" d="M13.5858 3.58579C14.3668 2.80474 15.6332 2.80474 16.4142 3.58579C17.1953 4.36683 17.1953 5.63316 16.4142 6.41421L15.6213 7.20711L12.7929 4.37868L13.5858 3.58579Z" fill="#111827"/>
				<path class="fill-muted" d="M11.3787 5.79289L3 14.1716V17H5.82842L14.2071 8.62132L11.3787 5.79289Z" fill="#111827"/>
			</svg>
		</a-button>
		<p class="text-dark">
			Site industriel principal spécialisé dans la production automobile. 
			Équipé de systèmes de monitoring énergétique avancés et de solutions d'optimisation automatisée. 
			Certification ISO 50001 obtenue en 2023.
		</p>
		<hr class="my-25">
		<a-descriptions title="Site Nord - Production" :column="1">
			<a-descriptions-item label="Responsable Énergie">
				Thomas Martin
			</a-descriptions-item>
			<a-descriptions-item label="Contact">
				+33 1 23 45 67 89
			</a-descriptions-item>
			<a-descriptions-item label="Email">
				t.martin@entreprise.com
			</a-descriptions-item>
			<a-descriptions-item label="Localisation">
				Zone Industrielle Nord, 75001 Paris
			</a-descriptions-item>
			<a-descriptions-item label="Surface">
				25,000 m²
			</a-descriptions-item>
			<a-descriptions-item label="Capacité Électrique">
				2,500 kVA
			</a-descriptions-item>
			<a-descriptions-item label="Certifications">
				<a-tag color="green">ISO 50001</a-tag>
				<a-tag color="blue">ISO 14001</a-tag>
				<a-tag color="purple">BREEAM</a-tag>
			</a-descriptions-item>
			<a-descriptions-item label="KPIs">
				<div class="kpi-list">
					<div class="kpi-item">
						<span class="label">Efficacité</span>
						<span class="value success">92%</span>
					</div>
					<div class="kpi-item">
						<span class="label">CO2</span>
						<span class="value warning">-15%</span>
					</div>
					<div class="kpi-item">
						<span class="label">ROI</span>
						<span class="value success">2.4</span>
					</div>
				</div>
			</a-descriptions-item>
		</a-descriptions>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
			siteInfo: {
				name: "Site Nord - Production",
				manager: "Thomas Martin",
				contact: "+33 1 23 45 67 89",
				email: "t.martin@entreprise.com",
				location: "Zone Industrielle Nord, 75001 Paris",
				surface: "25,000 m²",
				power: "2,500 kVA",
				certifications: ["ISO 50001", "ISO 14001", "BREEAM"],
				kpis: {
					efficiency: 92,
					co2Reduction: -15,
					roi: 2.4
				}
			}
		}
	},
})
</script>

<style scoped>
.card-site-information {
	background: white;
}

.text-dark {
	color: #111827;
	line-height: 1.6;
}

:deep(.ant-descriptions-title) {
	font-size: 18px;
	font-weight: 600;
	color: #1890ff;
}

:deep(.ant-descriptions-item-label) {
	color: #666;
	font-weight: 500;
}

:deep(.ant-descriptions-item-content) {
	color: #111827;
	font-weight: 500;
}

.kpi-list {
	display: flex;
	gap: 24px;
}

.kpi-item {
	display: flex;
	flex-direction: column;
	align-items: center;
}

.kpi-item .label {
	font-size: 12px;
	color: #666;
	margin-bottom: 4px;
}

.kpi-item .value {
	font-size: 16px;
	font-weight: 600;
}

.value.success {
	color: #52c41a;
}

.value.warning {
	color: #faad14;
}

:deep(.ant-tag) {
	margin: 4px;
	padding: 4px 8px;
}

.my-25 {
	margin: 25px 0;
	border-color: #f0f0f0;
}
</style>