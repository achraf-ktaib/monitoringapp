<template>
	<!-- Energy Project Card -->
	<a-card class="card-project">
		<img
			slot="cover"
			alt="projet-energie"
			:src="cover"
		/>
		<div class="card-tag" :class="statusClass">{{ status }}</div>
		<h5>{{ title }}</h5>
		<div class="project-metrics">
			<div class="metric">
				<span class="label">Économies</span>
				<div class="value-container">
					<span class="value">{{ savings }} kWh/an</span>
					<span class="sub-value">{{ co2Savings }} tCO2</span>
				</div>
			</div>
			<div class="metric">
				<span class="label">ROI</span>
				<div class="value-container">
					<span class="value">{{ roi }} ans</span>
					<span class="sub-value">{{ (1/roi * 100).toFixed(1) }}%/an</span>
				</div>
			</div>
			<div class="metric">
				<span class="label">Budget</span>
				<div class="value-container">
					<span class="value">{{ budget }}k€</span>
					<span class="sub-value">{{ (budget/savings).toFixed(2) }}€/kWh</span>
				</div>
			</div>
		</div>
		<div class="energy-impact">
			<div class="impact-header">
				<span>Impact Énergétique</span>
				<a-tag :color="impactColor">{{ impactLevel }}</a-tag>
			</div>
			<p class="description">{{ description }}</p>
		</div>
		<div class="progress-section">
			<div class="progress-header">
				<div class="progress-info">
					<span>Progression</span>
					<span class="phase">Phase: {{ currentPhase }}</span>
				</div>
				<span class="progress-value">{{ progress }}%</span>
			</div>
			<a-progress :percent="progress" :status="progressStatus" size="small" />
			<div class="milestone" v-if="nextMilestone">
				<a-icon type="calendar" />
				<span>Prochaine étape: {{ nextMilestone }}</span>
			</div>
		</div>
		<a-row type="flex" :gutter="6" class="card-footer" align="middle">
			<a-col :span="12">
				<a-button type="primary" size="small">VOIR DÉTAILS</a-button>
			</a-col>
			<a-col :span="12" class="text-right">
				<div class="team-info">
					<div class="deadline-container">
						<span class="deadline">Échéance: {{ deadline }}</span>
						<span class="remaining-days" v-if="daysRemaining">{{ daysRemaining }} jours restants</span>
					</div>
					<a-space :size="-12" class="avatar-chips">
						<a-tooltip v-for="(member, index) in team" :key="index" :title="member.role">
							<a-avatar size="small" :src="member.avatar" />
						</a-tooltip>
					</a-space>
				</div>
			</a-col>
		</a-row>
	</a-card>
</template>

<script>
export default ({
	props: {
		id: {
			type: Number,
			required: true,
		},
		title: {
			type: String,
			default: "",
		},
		description: {
			type: String,
			default: "",
		},
		cover: {
			type: String,
			default: "",
		},
		team: {
			type: Array,
			default: () => [],
		},
		status: {
			type: String,
			default: "En cours",
		},
		savings: {
			type: Number,
			default: 0,
		},
		roi: {
			type: Number,
			default: 0,
		},
		budget: {
			type: Number,
			default: 0,
		},
		progress: {
			type: Number,
			default: 0,
		},
		deadline: {
			type: String,
			default: "",
		},
		co2Savings: {
			type: Number,
			default: 0
		},
		impactLevel: {
			type: String,
			default: "Moyen"
		},
		currentPhase: {
			type: String,
			default: "Étude"
		},
		nextMilestone: {
			type: String,
			default: ""
		},
		daysRemaining: {
			type: Number,
			default: 0
		}
	},
	computed: {
		statusClass() {
			return {
				'status-active': this.status === 'En cours',
				'status-completed': this.status === 'Terminé',
				'status-planned': this.status === 'Planifié'
			}
		},
		progressStatus() {
			if (this.progress >= 100) return 'success'
			if (this.progress >= 70) return 'active'
			return 'normal'
		},
		impactColor() {
			const colors = {
				"Très élevé": "#f5222d",
				"Élevé": "#fa8c16",
				"Moyen": "#1890ff",
				"Faible": "#52c41a"
			}
			return colors[this.impactLevel] || "#1890ff"
		}
	}
})
</script>

<style scoped>
.card-project {
	border-radius: 12px;
	overflow: hidden;
}

.card-project img {
	height: 200px;
	object-fit: cover;
}

.card-tag {
	position: absolute;
	top: 16px;
	right: 16px;
	padding: 4px 12px;
	border-radius: 16px;
	font-size: 12px;
	font-weight: 600;
	color: white;
}

.status-active {
	background: #1890ff;
}

.status-completed {
	background: #52c41a;
}

.status-planned {
	background: #722ed1;
}

h5 {
	margin: 16px 0;
	font-size: 16px;
	font-weight: 600;
	color: #111827;
}

.project-metrics {
	display: grid;
	grid-template-columns: repeat(3, 1fr);
	gap: 12px;
	margin-bottom: 16px;
}

.metric {
	display: flex;
	flex-direction: column;
	align-items: center;
	text-align: center;
}

.metric .label {
	font-size: 12px;
	color: #666;
	margin-bottom: 4px;
}

.metric .value {
	font-size: 14px;
	font-weight: 600;
	color: #111827;
}

.description {
	color: #666;
	font-size: 14px;
	line-height: 1.5;
	margin-bottom: 16px;
}

.progress-section {
	margin-bottom: 16px;
}

.progress-header {
	display: flex;
	justify-content: space-between;
	margin-bottom: 8px;
	font-size: 14px;
	color: #666;
}

.card-footer {
	margin-top: 16px;
}

.team-info {
	display: flex;
	align-items: center;
	justify-content: flex-end;
	gap: 12px;
}

.deadline {
	font-size: 12px;
	color: #666;
}

:deep(.ant-progress-bg) {
	height: 6px !important;
}

.avatar-chips {
	display: flex;
	align-items: center;
}

:deep(.ant-avatar) {
	border: 2px solid white;
}

.value-container {
	display: flex;
	flex-direction: column;
	align-items: center;
}

.sub-value {
	font-size: 11px;
	color: #8c8c8c;
	margin-top: 2px;
}

.energy-impact {
	margin-bottom: 16px;
}

.impact-header {
	display: flex;
	justify-content: space-between;
	align-items: center;
	margin-bottom: 8px;
}

.milestone {
	display: flex;
	align-items: center;
	gap: 8px;
	margin-top: 8px;
	font-size: 12px;
	color: #666;
}

.phase {
	font-size: 12px;
	color: #1890ff;
	margin-left: 8px;
}

.progress-info {
	display: flex;
	align-items: center;
}

.deadline-container {
	display: flex;
	flex-direction: column;
	align-items: flex-end;
}

.remaining-days {
	font-size: 11px;
	color: #1890ff;
}

:deep(.ant-tag) {
	border-radius: 4px;
	font-weight: 500;
}
</style>