<script lang="ts" context="module">
	const API = 'https://api.themoviedb.org/3/search';
	const API_KEY = import.meta.env.VITE_API_KEY;
	export async function load({ fetch, params }: { fetch: any; params: any }) {
		const res = await fetch(`${API}/movie?api_key=${API_KEY}&query=${params.id}`);
		const data = await res.json();
		if (res.ok) {
			return { props: { search: data.results } };
		}
	}
</script>

<script lang="ts">
	import Movies from '../../components/Movies.svelte';
	export let search: any;
</script>

<section><Movies movies={search} /></section>
