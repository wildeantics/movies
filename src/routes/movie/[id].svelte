<script lang="ts" context="module">
	const API = import.meta.env.VITE_TMDB_API;
	const API_KEY = import.meta.env.VITE_API_KEY;
	export async function load({ fetch, params }) {
		console.log(params);
		const res = await fetch(`${API}/${params.id}?api_key=${API_KEY}`);
		const data = await res.json();
		console.log(data);
		if (res.ok) {
			return { props: { data } };
		}
	}
</script>
