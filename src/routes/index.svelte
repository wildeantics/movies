<script lang="ts" context="module">
	const API = import.meta.env.VITE_TMDB_API;
	const API_KEY = import.meta.env.VITE_API_KEY;
	export async function load({ fetch }: { fetch: any }) {
		const res = await fetch(`${API}/popular?api_key=${API_KEY}`);
		const data = await res.json();
		if (res.ok) {
			return { props: { popular: data.results } };
		}
	}
</script>

<script>
	import Popular from './../components/Popular.svelte';
	export let popular;
	console.log(popular);
</script>

<section><Popular {popular} /></section>
