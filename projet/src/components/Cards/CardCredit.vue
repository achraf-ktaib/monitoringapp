<template>
	<!-- Energy Summary Card -->
	<a-card class="card-energy header-solid h-full" :style="{ background: 'linear-gradient(135deg, #1a237e 0%, #0d47a1 100%)' }">
		<template #title>
			<svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" viewBox="0 0 24 24" fill="none" stroke="white">
				<path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 10V3L4 14h7v7l9-11h-7z"/>
			</svg>
		</template>
		<h5 class="total-consumption">2,456,789 kWh</h5>
		
		<div class="card-footer">
			<div class="mr-30">
				<p>Période</p>
				<h6>Janvier 2024</h6>
			</div>
			<div class="mr-30">
				<p>Variation</p>
				<h6 class="text-success">-8.5%</h6>
			</div>
			<div class="card-footer-col efficiency-rating ml-auto">
				<p>Score Efficacité</p>
				<h6 class="rating">A+</h6>
			</div>
		</div>
	</a-card>
</template>

<script>
export default ({
	data() {
		return {
			currentMonth: 'Janvier 2024',
			totalConsumption: '2,456,789',
			variation: -8.5,
			efficiencyRating: 'A+'
		}
	}
})
</script>

<style scoped>
.card-energy {
	color: white;
	padding: 20px;
	position: relative;
	overflow: hidden;
}

.total-consumption {
	font-size: 28px;
	font-weight: 700;
	margin: 25px 0;
	letter-spacing: 1px;
}

.card-footer {
	display: flex;
	align-items: center;
	margin-top: 30px;
}

.card-footer p {
	font-size: 12px;
	opacity: 0.8;
	margin-bottom: 5px;
}

.card-footer h6 {
	font-size: 16px;
	font-weight: 600;
	margin: 0;
}

.text-success {
	color: #4caf50;
}

.efficiency-rating {
	text-align: center;
	background: rgba(255, 255, 255, 0.1);
	padding: 8px 15px;
	border-radius: 8px;
}

.efficiency-rating .rating {
	font-size: 24px;
	font-weight: 700;
	color: #4caf50;
}

.mr-30 {
	margin-right: 30px;
}

.ml-auto {
	margin-left: auto;
}
</style>