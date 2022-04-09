<script context="module">
	// import dayjs from 'dayjs'
	// import customParseFormat from 'dayjs/plugin/customParseFormat'
	// import minMax from 'dayjs/plugin/minMax'

	// dayjs.extend(customParseFormat)
	// dayjs.extend(minMax)

	// load frontmatter for all posts
	export async function load() {
		// returns an object of every file of the type on that filepath
		const posts = import.meta.globEager('../../posts/*.md')
		// returns an array of values from the object
		const postsList = Object.values(posts)
		const postsMeta = postsList.map((post) => {
			return post.metadata
		})

		// load default post to render on posts page load
		const newest = postsMeta.sort((a, b) => {
			const c = new Date(a.date).getTime()
			const d = new Date(b.date).getTime()

			return d - c
		})

		const Post = await import(`../../posts/${postsMeta[0].slug}.md`)
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
