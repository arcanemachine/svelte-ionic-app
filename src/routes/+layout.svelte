<script lang="ts">
	import { dev } from '$app/environment';
	import { prefetchRoutes } from '$app/navigation';

	import { pwaStatusStream, type PWAStatus } from '$lib/services/pwa';

	// import Menu from '$lib/components/Menu.svelte';

	import { setupIonicSvelte } from '$ionic/svelte';

	/* Theme variables */
	import '../theme/variables.css';

	setupIonicSvelte();

	pwaStatusStream.subscribe((status: PWAStatus) => {
		console.log('PWA status', status);

		if (status.updateFunction) {
			console.log('PWA updating itself in 4 secs......');
			setTimeout(() => {
				status.updateFunction();
			}, 4000);
		}
	});

	// Aggressive prefetching for faster rendering
	if (!dev) {
		prefetchRoutes();
	}
</script>

<ion-app>
	<ion-header>
		<ion-toolbar>
			<ion-title>Hello Ionic!</ion-title>
		</ion-toolbar>
	</ion-header>

	<ion-content class="ion-padding">
		<slot />
	</ion-content>
</ion-app>
