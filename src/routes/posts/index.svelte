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
				DefaultPost: Post.default
			}
		}
	}
</script>

<script>
	export let DefaultPost
</script>

<h1>Latest Sick Beat</h1>

<svelte:component this={DefaultPost} />

<style>
	h1 {
		color: #e4e4e4;
		margin-bottom: 1em;
	}
</style>
