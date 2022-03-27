<script>
	import '../app.css'
	import Header from '$lib/Header.svelte'
</script>

<Header />

<main class="bg-dark">
	<slot />
</main>

<footer>&copy; Orange Cat Media 2022</footer>

<style>
	main,
	footer {
		width: min(100% - 2rem, 60rem);
		margin-inline: auto;
		text-align: center;
	}

	footer {
		font-family: 'Fraunces', serif;
	}
</style>
