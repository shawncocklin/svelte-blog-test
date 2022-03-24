<script context="module">
	export function load({ error, status }) {
		return {
			props: {
				status,
				error
			}
		}
	}
</script>

<script>
	export let status
	export let error
</script>

<h1>Uhh Ohh...</h1>

<h3>{`${status}: ${error.message}`}</h3>
