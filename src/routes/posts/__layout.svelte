<script context="module">
	// load all posts
	export async function load() {
		// returns an object of every file of the type on that filepath
		const posts = import.meta.globEager('../../posts/*.md')
		// returns an array of values from the object
		const postsList = Object.values(posts)
		const postsMeta = postsList.map((post) => {
			return post.metadata
		})

		// load default post to render on posts page load
		// TODO: pull date value and compare to a new Date() object to reference the newest post
		const date = postsMeta.map((post) => {
			return post.date
		})
		const index = date.indexOf('first')

		const Post = await import(`../../posts/${postsMeta[index].slug}.md`)

		return {
			props: {
				posts: postsMeta,
				DefaultPost: Post.default
			}
		}
	}
</script>

<script>
	export let posts
	const base = '../../posts/'
	import '../../app.css'
</script>

<div class="grid">
	<div class="text-left">
		<slot />
	</div>
	<aside>
		<h3>Archive</h3>
		<ul>
			{#each posts as post}
				<li>
					<a href="{base}{post.slug}">{post.title}</a>
				</li>
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
		color: #e4e4e4;
	}
</style>
