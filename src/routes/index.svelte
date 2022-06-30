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
	import Movies from '../components/Movies.svelte';
	import { blur } from 'svelte/transition';
	export let popular;
</script>

<section in:blur={{ x: 0, duration: 500 }} out:blur={{ x: 0, duration: 300 }}>
	<Movies movies={popular} />
</section>
