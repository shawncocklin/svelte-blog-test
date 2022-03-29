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
		margin-inline: auto;
		text-align: center;
	}

	main {
		width: min(100% - 2rem, 60rem);
	}

	footer {
		font-family: 'Fraunces', serif;
		background-color: #e4e4e4;
		color: #423221;
		min-height: 5vh;
		width: 100%;
		position: absolute;
		bottom: 0;
	}
</style>
