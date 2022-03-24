<script context="module">
	// loads server side data before rendering any of the components
	export async function load({ params }) {
		try {
			const Post = await import(`../../posts/${params.slug}.md`)
			return {
				// data passed into the component
				props: {
					Post: Post.default
				}
			}
		} catch (error) {
			return {
				status: 404,
				error: 'Page Not Found'
			}
		}
	}
</script>

<script>
	export let Post
</script>

<svelte:component this={Post} />
