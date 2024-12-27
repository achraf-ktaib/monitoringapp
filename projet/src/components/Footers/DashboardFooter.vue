<template>
	
	<!-- Layout Footer -->
	<a-layout-footer>
		<a-row type="flex">
			<a-col :span="24" :md="12">

				<!-- Footer Copyright Notice -->
				<p class="copyright">
					© 2024, EnergyMonitor
					<svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
						<path fill-rule="evenodd" clip-rule="evenodd" d="M3.17157 5.17157C4.73367 3.60948 7.26633 3.60948 8.82843 5.17157L10 6.34315L11.1716 5.17157C12.7337 3.60948 15.2663 3.60948 16.8284 5.17157C18.3905 6.73367 18.3905 9.26633 16.8284 10.8284L10 17.6569L3.17157 10.8284C1.60948 9.26633 1.60948 6.73367 3.17157 5.17157Z" fill="#4CAF50"/>
					</svg>
					Votre partenaire en efficacité énergétique
				</p>
				<!-- / Footer Copyright Notice -->

			</a-col>
			<a-col :span="24" :md="12" class="footer-control">

				<!-- Footer Navigation Menu -->
				<a-menu mode="horizontal">
					<a-menu-item>Tableau de bord</a-menu-item>
					<a-menu-item>Support 24/7</a-menu-item>
					<a-menu-item>Centre d'aide</a-menu-item>
					<a-menu-item>Mentions légales</a-menu-item>
				</a-menu>
				<!-- / Footer Navigation Menu -->

			</a-col>
		</a-row>
	</a-layout-footer>
	<!-- / Layout Footer -->

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
.copyright {
	color: #8C8C8C;
	font-size: 14px;
}

.footer-control {
	display: flex;
	justify-content: flex-end;
}

.ant-menu {
	background: transparent;
	border: none;
}

.ant-menu-item {
	color: #8C8C8C;
}

.ant-menu-item:hover {
	color: #4CAF50 !important;
}

.ant-layout-footer {
	background: #FFFFFF;
	padding: 24px;
	border-top: 1px solid #f0f0f0;
}
</style>
