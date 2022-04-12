<script>
	function preload(src) {
		return new Promise((res) => {
			let img = new Image()
			img.onload = res
			img.src = src
		})
	}

	let src = 'https://source.unsplash.com/random/400x300?music'
</script>

<!-- TODO: adjust hero copy -->

{#await preload(src) then}
	<div class="flow">
		<h2>Welcome to Sick Beats</h2>
		<p>
			Join me as I rate, review, and overanalyze the songs on my <a
				class="underline"
				href="https://open.spotify.com/playlist/0fyjsVZmoLbRrDI8CrBi2s?si=75a5fbff793a4938"
				>Spotify playlist</a
			>
		</p>

		<img {src} alt="" />
	</div>
{/await}

<style>
	div {
		color: #e4e4e4;
		display: flex;
		flex-direction: column;
	}

	h2 {
		font-size: clamp(1.5rem, 2.4vw + 1rem, 2.5rem);
	}

	p {
		font-size: clamp(1rem, 1.2vw + 0.8rem, 1.5rem);
	}

	img {
		border-radius: 20px;
	}

	.flow > * + * {
		margin-top: max(1.25em, 30px);
	}

	.underline {
		text-decoration: underline;
	}
</style>
