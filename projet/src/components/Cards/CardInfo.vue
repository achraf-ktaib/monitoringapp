<template>
	<a-card :bordered="false" class="card-info">
		<a-row type="flex">
			<a-col class="col-content" :span="24" :xl="12">
				<div class="card-content">
					<h6>Objectifs Énergétiques 2024</h6>
					<h5>Programme d'Efficacité Énergétique</h5>
					<p>Notre engagement pour une réduction de 25% de la consommation énergétique. Découvrez nos solutions et recommandations pour atteindre cet objectif.</p>
					
					<div class="key-metrics">
						<div class="metric">
							<span class="label">Objectif Annuel</span>
							<span class="value">-25%</span>
						</div>
						<div class="metric">
							<span class="label">Progrès Actuel</span>
							<span class="value success">-15%</span>
						</div>
						<div class="metric">
							<span class="label">Économies Réalisées</span>
							<span class="value">125K€</span>
						</div>
					</div>
				</div>
				<div class="card-footer">
					<a href="#" class="view-details">
						<span>Voir le Plan Détaillé</span>
						<svg width="16" height="16" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
							<path fill-rule="evenodd" clip-rule="evenodd" d="M7.29289 14.7071C6.90237 14.3166 6.90237 13.6834 7.29289 13.2929L10.5858 10L7.29289 6.70711C6.90237 6.31658 6.90237 5.68342 7.29289 5.29289C7.68342 4.90237 8.31658 4.90237 8.70711 5.29289L12.7071 9.29289C13.0976 9.68342 13.0976 10.3166 12.7071 10.7071L8.70711 14.7071C8.31658 15.0976 7.68342 15.0976 7.29289 14.7071Z" fill="#1890ff"/>
						</svg>
					</a>
				</div>
			</a-col>
			<a-col class="col-img" :span="24" :xl="12">
				<div class="card-img-bg">
					<div class="energy-progress-chart">
						<div class="chart-circle">
							<svg viewBox="0 0 36 36" class="circular-chart">
								<path d="M18 2.0845
									a 15.9155 15.9155 0 0 1 0 31.831
									a 15.9155 15.9155 0 0 1 0 -31.831"
									fill="none"
									stroke="#eee"
									stroke-width="3"/>
								<path d="M18 2.0845
									a 15.9155 15.9155 0 0 1 0 31.831
									a 15.9155 15.9155 0 0 1 0 -31.831"
									fill="none"
									stroke="#1890ff"
									stroke-width="3"
									stroke-dasharray="60, 100"/>
							</svg>
							<div class="percentage">60%</div>
						</div>
						<div class="progress-label">Progression vers l'objectif</div>
					</div>
				</div>
			</a-col>
		</a-row>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
			progressPercentage: 60
		}
	},
})
</script>

<style scoped>
.card-info {
	background: #ffffff;
	border-radius: 12px;
}

.card-content {
	padding: 24px;
}

.card-content h6 {
	color: #1890ff;
	font-size: 14px;
	margin-bottom: 8px;
}

.card-content h5 {
	font-size: 24px;
	font-weight: 600;
	margin-bottom: 16px;
}

.card-content p {
	color: #666;
	line-height: 1.6;
}

.key-metrics {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	gap: 16px;
	margin-top: 24px;
}

.metric {
	display: flex;
	flex-direction: column;
	gap: 4px;
}

.metric .label {
	font-size: 12px;
	color: #666;
}

.metric .value {
	font-size: 18px;
	font-weight: 600;
	color: #111827;
}

.metric .value.success {
	color: #52c41a;
}

.card-footer {
	padding: 16px 24px;
	border-top: 1px solid #f0f0f0;
}

.view-details {
	display: flex;
	align-items: center;
	gap: 8px;
	color: #1890ff;
	text-decoration: none;
	font-weight: 500;
}

.energy-progress-chart {
	display: flex;
	flex-direction: column;
	align-items: center;
	justify-content: center;
	height: 100%;
	padding: 24px;
}

.chart-circle {
	position: relative;
	width: 200px;
	height: 200px;
}

.circular-chart {
	width: 100%;
	height: 100%;
}

.percentage {
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	font-size: 24px;
	font-weight: 600;
	color: #1890ff;
}

.progress-label {
	margin-top: 16px;
	font-size: 14px;
	color: #666;
	text-align: center;
}

.col-img {
	background: #f8f9fa;
	border-radius: 0 12px 12px 0;
}

@media (max-width: 1200px) {
	.col-img {
		border-radius: 0 0 12px 12px;
	}
}
</style>