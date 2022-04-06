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
		// TODO: install dayjs to see if this works
		const date = postsMeta.map((post) => {
			return post.date
		})

		// // returns the most recent date of the given parameters
		// const newest = dayjs.max(...date)

		const index = date.indexOf('first') // remember to remove this

		const Post = await import(`../../posts/${postsMeta[index].slug}.md`) // remember to change index to newest

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
