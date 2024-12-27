<template>
	<!-- Energy Events Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{paddingTop: 0, paddingBottom: '16px' }">
		<template #title>
			<h6 class="font-semibold m-0">Événements Énergétiques</h6>
		</template>
		<p slot="extra" class="card-header-date">
			<a-icon type="calendar" />
			<span>{{ currentPeriod }}</span>
		</p>
		<a-list
			class="events-list"
			item-layout="horizontal"
			:split="false"
			:data-source="data"
		>
			<a-list-item slot="renderItem" slot-scope="item">
				<template v-if="item.period">
					<h6>{{ item.period }}</h6>
				</template>
				<template v-else>
					<a-list-item-meta
						:title="item.title"
						:description="item.datetime"
					>
						<!-- Pic de consommation -->
						<a-avatar size="small" v-if="item.type === 'peak'" slot="avatar" style="background-color: #FEE9EA">
							<svg width="10" height="10" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
								<path class="fill-danger" d="M10 3l6 12H4l6-12z" fill="#f5222d"/>
							</svg>
						</a-avatar>
						<!-- Économie d'énergie -->
						<a-avatar size="small" v-if="item.type === 'saving'" slot="avatar" style="background-color: #EDF9E7">
							<svg width="10" height="10" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
								<path class="fill-success" d="M16 10l-4-4v3H4v2h8v3l4-4z" fill="#52c41a"/>
							</svg>
						</a-avatar>
						<!-- Alerte -->
						<a-avatar size="small" v-if="item.type === 'alert'" slot="avatar" style="background-color: #FFFCE7">
							<strong class="text-warning">!</strong>
						</a-avatar>
						<!-- Maintenance -->
						<a-avatar size="small" v-if="item.type === 'maintenance'" slot="avatar" style="background-color: #E6F7FF">
							<svg width="10" height="10" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
								<path class="fill-info" d="M13 7h-6v6h6v-6z" fill="#1890ff"/>
							</svg>
						</a-avatar>
					</a-list-item-meta>
					<div class="event-value">
						<template v-if="item.type === 'peak'">
							<span class="text-danger">{{ item.value }} kWh</span>
						</template>
						<template v-if="item.type === 'saving'">
							<span class="text-success">-{{ item.value }} kWh</span>
						</template>
						<template v-if="item.type === 'alert'">
							<span class="text-warning">{{ item.value }}</span>
						</template>
						<template v-if="item.type === 'maintenance'">
							<span class="text-info">{{ item.value }}</span>
						</template>
					</div>
				</template>
			</a-list-item>
		</a-list>
	</a-card>
</template>

<script>
export default ({
	props: {
		data: {
			type: Array,
			default: () => [],
		},
	},
	data() {
		return {
			currentPeriod: this.getCurrentPeriod()
		}
	},
	methods: {
		getCurrentPeriod() {
			const now = new Date()
			const start = new Date(now.getTime() - 7 * 24 * 60 * 60 * 1000)
			return `${start.toLocaleDateString('fr-FR')} - ${now.toLocaleDateString('fr-FR')}`
		}
	}
})
</script>

<style scoped>
.events-list {
	margin-top: 8px;
}

:deep(.ant-list-item) {
	padding: 12px 24px;
}

:deep(.ant-list-item-meta-title) {
	font-size: 14px;
	color: #111827;
	margin-bottom: 0;
}

:deep(.ant-list-item-meta-description) {
	font-size: 12px;
	color: #666;
}

.card-header-date {
	display: flex;
	align-items: center;
	gap: 8px;
	color: #666;
	font-size: 14px;
}

.event-value {
	font-weight: 600;
	font-size: 14px;
}

.text-danger {
	color: #f5222d;
}

.text-success {
	color: #52c41a;
}

.text-warning {
	color: #faad14;
}

.text-info {
	color: #1890ff;
}

:deep(.ant-avatar) {
	display: flex;
	align-items: center;
	justify-content: center;
}

h6 {
	color: #1890ff;
	font-size: 12px;
	text-transform: uppercase;
	margin: 8px 0;
}
</style>