<script context="module">
	export async function load() {
		// returns an object of every file of the type on that filepath
		const posts = import.meta.globEager('../../posts/*.md')
		// returns an array of values from the object
		const postsList = Object.values(posts)
		const postsMeta = postsList.map((post) => {
			return post.metadata
		})

		return {
			props: {
				posts: postsMeta
			}
		}
	}
</script>

<script>
	export let posts
	const base = '../../posts/'
</script>

<div class="grid">
	<div class="text-left">
		<slot />
	</div>
	<aside>
		<h3>Archive</h3>
		<ul>
			{#each posts as post}
				<li><a href="{base}{post.slug}">{post.title}</a></li>
			{/each}
		</ul>
	</aside>
</div>

<style>
	.grid {
		display: grid;
		grid-template-columns: 3fr 1fr;
		gap: 5rem;
	}

	.text-left {
		text-align: left;
	}

	li {
		list-style: none;
		text-align: left;
	}

	h3 {
		color: #fafafa;
	}
</style>
