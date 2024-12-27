<template>
	<!-- Energy Reports Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{paddingTop: 0, paddingBottom: '16px' }">
		<template #title>
			<h6 class="font-semibold m-0">Rapports Énergétiques</h6>
		</template>
		<template slot="extra" class="mb-0">
			<a-button type="primary">
				VOIR TOUT
			</a-button>
		</template>
		<a-list
			class="reports-list"
			item-layout="horizontal"
			:split="false"
			:data-source="data"
		>
			<a-list-item slot="renderItem" slot-scope="item">
				<a-button slot="actions" type="link" class="download-btn">
					<svg width="15" height="15" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path fill-rule="evenodd" clip-rule="evenodd" d="M3 17C3 16.4477 3.44772 16 4 16H16C16.5523 16 17 16.4477 17 17C17 17.5523 16.5523 18 16 18H4C3.44772 18 3 17.5523 3 17ZM6.29289 9.29289C6.68342 8.90237 7.31658 8.90237 7.70711 9.29289L9 10.5858L9 3C9 2.44772 9.44771 2 10 2C10.5523 2 11 2.44771 11 3L11 10.5858L12.2929 9.29289C12.6834 8.90237 13.3166 8.90237 13.7071 9.29289C14.0976 9.68342 14.0976 10.3166 13.7071 10.7071L10.7071 13.7071C10.5196 13.8946 10.2652 14 10 14C9.73478 14 9.48043 13.8946 9.29289 13.7071L6.29289 10.7071C5.90237 10.3166 5.90237 9.68342 6.29289 9.29289Z" fill="#1890ff"/>
					</svg>
					RAPPORT
				</a-button>
				<a-list-item-meta
					:title="item.title"
					:description="item.period"
				>
					<template #avatar>
						<div :class="['consumption-indicator', item.trend]">
							<span class="percentage">{{ item.variation }}</span>
						</div>
					</template>
				</a-list-item-meta>
				<div class="consumption">{{ item.consumption }} kWh</div>
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
					title: "Rapport Mensuel - Janvier 2024",
					period: "01/01/2024 - 31/01/2024",
					consumption: "45,678",
					variation: "-8.5%",
					trend: "decrease"
				},
				{
					title: "Rapport Mensuel - Décembre 2023",
					period: "01/12/2023 - 31/12/2023",
					consumption: "49,890",
					variation: "+2.1%",
					trend: "increase"
				},
				{
					title: "Rapport Mensuel - Novembre 2023",
					period: "01/11/2023 - 30/11/2023",
					consumption: "48,765",
					variation: "-5.2%",
					trend: "decrease"
				},
				{
					title: "Rapport Trimestriel - Q4 2023",
					period: "01/10/2023 - 31/12/2023",
					consumption: "144,333",
					variation: "-3.8%",
					trend: "decrease"
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
.reports-list {
	padding: 0 10px;
}

:deep(.ant-list-item) {
	padding: 16px 0;
	align-items: center;
}

:deep(.ant-list-item-meta) {
	align-items: center;
}

:deep(.ant-list-item-meta-title) {
	font-size: 14px;
	margin-bottom: 4px !important;
	color: #111827;
}

:deep(.ant-list-item-meta-description) {
	font-size: 12px;
	color: #6b7280;
}

.consumption-indicator {
	width: 40px;
	height: 40px;
	border-radius: 8px;
	display: flex;
	align-items: center;
	justify-content: center;
}

.consumption-indicator.decrease {
	background-color: #e6f7ff;
	color: #1890ff;
}

.consumption-indicator.increase {
	background-color: #fff1f0;
	color: #f5222d;
}

.percentage {
	font-size: 12px;
	font-weight: 600;
}

.consumption {
	font-size: 14px;
	font-weight: 600;
	color: #111827;
}

.download-btn {
	display: flex;
	align-items: center;
	gap: 4px;
	color: #1890ff;
}

:deep(.ant-list-item-action) {
	margin-left: 24px;
}

:deep(.ant-card-extra) {
	padding: 16px 0;
}
</style>