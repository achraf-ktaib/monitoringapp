<template>
	<!-- Energy Events Timeline Card -->
	<a-card :bordered="false" class="header-solid h-full" :bodyStyle="{paddingTop: '12px',}">
		<template #title>
			<h6>Historique des Événements</h6>			
			<p>ce mois-ci <span class="text-danger">+15%</span> d'incidents</p>	
		</template>
		<a-timeline pending="En cours d'enregistrement..." :reverse="timelineReverse">
			<a-timeline-item color="red">
				Alerte : Pic de consommation - Site Nord
				<p>15 JAN 14:20 - <span class="event-value">52,450 kWh</span></p>
			</a-timeline-item>
			<a-timeline-item color="green">
				Maintenance préventive effectuée - Unité 3
				<p>14 JAN 09:15 - <span class="event-value">Économie estimée: 8%</span></p>
			</a-timeline-item>
			<a-timeline-item color="blue">
				Mise à jour des objectifs énergétiques
				<p>12 JAN 11:30 - <span class="event-value">Nouvel objectif: 42,000 kWh/mois</span></p>
			</a-timeline-item>
			<a-timeline-item color="orange">
				Avertissement : Dérive de consommation - Site Est
				<p>10 JAN 16:45 - <span class="event-value">+12% vs objectif</span></p>
			</a-timeline-item>
			<a-timeline-item color="green">
				Installation nouveaux capteurs intelligents
				<p>08 JAN 10:20 - <span class="event-value">15 capteurs déployés</span></p>
			</a-timeline-item>
			<a-timeline-item color="blue">
				Rapport mensuel généré - Décembre 2023
				<p>05 JAN 08:30 - <span class="event-value">45,678 kWh consommés</span></p>
			</a-timeline-item>
			<template #pendingDot>
				<a-spin size="small" />
			</template>
		</a-timeline>
		<a-button type="primary" block size="small" @click="timelineReverse = !timelineReverse">
			<svg v-show="!timelineReverse" width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<path d="M3 3C2.44772 3 2 3.44772 2 4C2 4.55228 2.44772 5 3 5H14C14.5523 5 15 4.55228 15 4C15 3.44772 14.5523 3 14 3H3Z" fill="currentColor"/>
				<path d="M3 7C2.44772 7 2 7.44772 2 8C2 8.55228 2.44772 9 3 9H8C8.55228 9 9 8.55228 9 8C9 7.44772 8.55228 7 8 7H3Z" fill="currentColor"/>
				<path d="M3 11C2.44772 11 2 11.4477 2 12C2 12.5523 2.44772 13 3 13H7C7.55228 13 8 12.5523 8 12C8 11.4477 7.55228 11 7 11H3Z" fill="currentColor"/>
				<path d="M13 16C13 16.5523 13.4477 17 14 17C14.5523 17 15 16.5523 15 16L15 10.4142L16.2929 11.7071C16.6834 12.0976 17.3166 12.0976 17.7071 11.7071C18.0976 11.3166 18.0976 10.6834 17.7071 10.2929L14.7071 7.29289C14.5196 7.10536 14.2652 7 14 7C13.7348 7 13.4804 7.10536 13.2929 7.29289L10.2929 10.2929C9.90237 10.6834 9.90237 11.3166 10.2929 11.7071C10.6834 12.0976 11.3166 12.0976 11.7071 11.7071L13 10.4142L13 16Z" fill="currentColor"/>
			</svg>
			<svg v-show="timelineReverse" width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
				<path d="M3 3C2.44772 3 2 3.44772 2 4C2 4.55228 2.44772 5 3 5H14C14.5523 5 15 4.55228 15 4C15 3.44772 14.5523 3 14 3H3Z" fill="currentColor"/>
				<path d="M3 7C2.44772 7 2 7.44772 2 8C2 8.55228 2.44772 9 3 9H10C10.5523 9 11 8.55228 11 8C11 7.44772 10.5523 7 10 7H3Z" fill="currentColor"/>
				<path d="M3 11C2.44772 11 2 11.4477 2 12C2 12.5523 2.44772 13 3 13H7C7.55228 13 8 12.5523 8 12C8 11.4477 7.55228 11 7 11H3Z" fill="currentColor"/>
				<path d="M15 8C15 7.44772 14.5523 7 14 7C13.4477 7 13 7.44771 13 8L13 13.5858L11.7071 12.2929C11.3166 11.9024 10.6834 11.9024 10.2929 12.2929C9.90237 12.6834 9.90237 13.3166 10.2929 13.7071L13.2929 16.7071C13.4804 16.8946 13.7348 17 14 17C14.2652 17 14.5196 16.8946 14.7071 16.7071L17.7071 13.7071C18.0976 13.3166 18.0976 12.6834 17.7071 12.2929C17.3166 11.9024 16.6834 11.9024 16.2929 12.2929L15 13.5858L15 8Z" fill="currentColor"/>
			</svg>
			INVERSER L'ORDRE
		</a-button>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
			timelineReverse: false,
		}
	},
})
</script>

<style scoped>
.header-solid h6 {
	margin-bottom: 4px;
}

:deep(.ant-timeline) {
	padding: 16px;
}

:deep(.ant-timeline-item-content) {
	margin-left: 32px;
}

:deep(.ant-timeline-item) {
	padding-bottom: 24px;
}

:deep(.ant-timeline-item-content) p {
	margin: 4px 0 0;
	font-size: 12px;
	color: #666;
}

.event-value {
	font-weight: 600;
	color: #111827;
}

:deep(.ant-timeline-item-head-red) {
	color: #f5222d;
	border-color: #f5222d;
}

:deep(.ant-timeline-item-head-orange) {
	color: #fa8c16;
	border-color: #fa8c16;
}

:deep(.ant-timeline-item-head-green) {
	color: #52c41a;
	border-color: #52c41a;
}

:deep(.ant-timeline-item-head-blue) {
	color: #1890ff;
	border-color: #1890ff;
}

.text-danger {
	color: #f5222d;
}

:deep(.ant-btn-primary) {
	display: flex;
	align-items: center;
	justify-content: center;
	gap: 8px;
	margin-top: 8px;
}
</style>