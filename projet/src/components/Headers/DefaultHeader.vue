<template>

	<!-- Layout Header ( Navbar ) -->
	<a-layout-header>
		<div class="header-col header-brand">
			<h6>EnergyMonitor Dashboard</h6>

			<!-- Trigger Button For Navigation Menu For Small Screens -->
			<a-button type="link" @click="collapseNav = collapseNav ? 0 : 1" class="btn-menu-trigger">
				<svg width="20" height="20" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512">
					<path d="M16 132h416c8.837 0 16-7.163 16-16V76c0-8.837-7.163-16-16-16H16C7.163 60 0 67.163 0 76v40c0 8.837 7.163 16 16 16zm0 160h416c8.837 0 16-7.163 16-16v-40c0-8.837-7.163-16-16-16H16c-8.837 0-16 7.163-16 16v40c0 8.837 7.163 16 16 16zm0 160h416c8.837 0 16-7.163 16-16v-40c0-8.837-7.163-16-16-16H16c-8.837 0-16 7.163-16 16v40c0 8.837 7.163 16 16 16z"/>
				</svg>
			</a-button>
			<!-- Trigger Button For Navigation Menu For Small Screens -->

		</div>
		<div class="header-col header-nav">

			<!-- Navigation Menu For Large Screens -->
			<a-menu mode="horizontal" class="menu-large">
				<a-menu-item>
					<router-link to="/dashboard" class="nav-link" @click="e => e.preventDefault()">
						<span>Tableau de bord</span>
					</router-link>
				</a-menu-item>
				<a-menu-item>
					<router-link to="/reports" class="nav-link" @click="e => e.preventDefault()">
						<span>Rapports</span>
					</router-link>
				</a-menu-item>
				<a-menu-item>
					<router-link to="/profile" class="nav-link" @click="e => e.preventDefault()">
						<span>Profil</span>
					</router-link>
				</a-menu-item>
				<a-menu-item>
					<router-link to="/sign-in" class="nav-link" @click="e => e.preventDefault()">
						<span>Se connecter</span>
					</router-link>
				</a-menu-item>
				<a-menu-item>
					<router-link to="/sign-up" class="nav-link" @click="e => e.preventDefault()">
						<span>S'inscrire</span>
					</router-link>
				</a-menu-item>
			</a-menu>
			<!-- / Navigation Menu For Large Screens -->

			<!-- Collapsible Navigation Menu For Small Screens -->
			<div class="menu-small">
				
				<!-- Collapsible Component For Navigation Menu For Small Screens -->
				<a-collapse v-model="collapseNav" accordion>
					<a-collapse-panel key="1">

						<!-- Navigation Menu For Small Screens -->
						<a-menu mode="vertical">
							<a-menu-item>
								<router-link to="/dashboard" class="nav-link" @click="e => e.preventDefault()">
									<span>Tableau de bord</span>
								</router-link>
							</a-menu-item>
							<a-menu-item>
								<router-link to="/reports" class="nav-link" @click="e => e.preventDefault()">
									<span>Rapports</span>
								</router-link>
							</a-menu-item>
							<a-menu-item>
								<router-link to="/profile" class="nav-link" @click="e => e.preventDefault()">
									<span>Profil</span>
								</router-link>
							</a-menu-item>
							<a-menu-item>
								<router-link to="/sign-in" class="nav-link" @click="e => e.preventDefault()">
									<span>Se connecter</span>
								</router-link>
							</a-menu-item>
							<a-menu-item>
								<router-link to="/sign-up" class="nav-link" @click="e => e.preventDefault()">
									<span>S'inscrire</span>
								</router-link>
							</a-menu-item>
						</a-menu>
						<!-- / Navigation Menu For Small Screens -->

					</a-collapse-panel>
				</a-collapse>
				<!-- / Collapsible Component For Navigation Menu For Small Screens -->

			</div>
			<!-- / Collapsible Navigation Menu For Small Screens -->

		</div>

	</a-layout-header>
	<!-- / Layout Header ( Navbar ) -->

</template>

<script>

	export default ({
		data() {
			return {
				// Collapse navigation value.
				collapseNav: 0,
			}
		},
	})

</script>

<style lang="scss" scoped>

	.header-col {
		display: flex;
		align-items: center;
	}

	.nav-link {
		color: #4CAF50; /* Couleur pour les liens */
	}

	.nav-link:hover {
		color: #2E7D32; /* Couleur au survol */
	}

</style>