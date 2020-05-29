<script>
	import TrainingDay from './components/TrainingDay.svelte'
	export let name;
</script>

<svelte:head>
	<title>{name}</title>
</svelte:head>

<main>
	<h1>{name}</h1>
	<TrainingDay />	
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
		text-align: justify;
	}

	h1 {
		color: purple;
		text-transform: uppercase;
		text-align: center;
		font-size: 4em;
		font-weight: 600;
		/* font-family: monospace; */
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>