<script lang="ts">
	// import { goto } from '$app/navigation';
	// goto('/components/Splash');

	let count = 0;

	function handleClick() {
		count += 1;
	}
</script>

<ion-content>
	<ion-grid>
		<ion-row class="ion-justify-content-center">
			<div>
				<ion-button on:click={handleClick}>Click Me!</ion-button>
			</div>
		</ion-row>
		<ion-row class="ion-justify-content-center">
			Count: {count}
		</ion-row>
	</ion-grid>
</ion-content>
