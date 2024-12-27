<template>
	<!-- Energy Tips Card -->
	<a-card :bordered="false" class="card-info-2 h-full">
		<div class="col-content h-full" :style="{ background: 'linear-gradient(135deg, #004d40 0%, #00695c 100%)' }">
			<div class="card-content">
				<div class="icon-wrapper">
					<svg xmlns="http://www.w3.org/2000/svg" width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="currentColor">
						<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z"/>
					</svg>
				</div>
				<h5>Recommandations d'Économie d'Énergie</h5>
				<div class="tips-list">
					<div class="tip-item">
						<span class="tip-badge">1</span>
						<p>Optimisation des horaires de production : -15% de consommation</p>
					</div>
					<div class="tip-item">
						<span class="tip-badge">2</span>
						<p>Maintenance préventive des équipements : +20% d'efficacité</p>
					</div>
					<div class="tip-item">
						<span class="tip-badge">3</span>
						<p>Installation de capteurs intelligents : Économies potentielles de 25%</p>
					</div>
				</div>
			</div>
			<div class="card-footer">
				<a-button type="primary" class="action-button" ghost>
					<span>Voir Toutes les Recommandations</span>
					<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path fill-rule="evenodd" clip-rule="evenodd" d="M7.29289 14.7071C6.90237 14.3166 6.90237 13.6834 7.29289 13.2929L10.5858 10L7.29289 6.70711C6.90237 6.31658 6.90237 5.68342 7.29289 5.29289C7.68342 4.90237 8.31658 4.90237 8.70711 5.29289L12.7071 9.29289C13.0976 9.68342 13.0976 10.3166 12.7071 10.7071L8.70711 14.7071C8.31658 15.0976 7.68342 15.0976 7.29289 14.7071Z" fill="currentColor"/>
					</svg>
				</a-button>
			</div>
		</div>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
			tips: [
				{
					id: 1,
					text: "Optimisation des horaires de production",
					impact: "-15% de consommation"
				},
				{
					id: 2,
					text: "Maintenance préventive des équipements",
					impact: "+20% d'efficacité"
				},
				{
					id: 3,
					text: "Installation de capteurs intelligents",
					impact: "Économies potentielles de 25%"
				}
			]
		}
	},
})
</script>

<style scoped>
.card-info-2 {
	overflow: hidden;
}

.col-content {
	color: white;
	padding: 24px;
	height: 100%;
	display: flex;
	flex-direction: column;
	justify-content: space-between;
}

.icon-wrapper {
	background: rgba(255, 255, 255, 0.1);
	width: 48px;
	height: 48px;
	border-radius: 12px;
	display: flex;
	align-items: center;
	justify-content: center;
	margin-bottom: 16px;
}

.card-content h5 {
	font-size: 20px;
	font-weight: 600;
	margin-bottom: 24px;
}

.tips-list {
	display: flex;
	flex-direction: column;
	gap: 16px;
}

.tip-item {
	display: flex;
	align-items: flex-start;
	gap: 12px;
	background: rgba(255, 255, 255, 0.1);
	padding: 12px;
	border-radius: 8px;
}

.tip-badge {
	background: #00897b;
	color: white;
	width: 24px;
	height: 24px;
	border-radius: 50%;
	display: flex;
	align-items: center;
	justify-content: center;
	font-weight: 600;
	flex-shrink: 0;
}

.tip-item p {
	margin: 0;
	font-size: 14px;
	line-height: 1.5;
}

.card-footer {
	margin-top: 24px;
}

.action-button {
	width: 100%;
	display: flex;
	align-items: center;
	justify-content: center;
	gap: 8px;
	height: 40px;
	border-color: rgba(255, 255, 255, 0.5);
	color: white;
}

.action-button:hover {
	border-color: white;
	color: white;
	background: rgba(255, 255, 255, 0.1);
}
</style>