<script>
	import Card from './Card.svelte';
	export let popular;
</script>

<h3>Popular Movies</h3>
<div class="cards">
	{#each popular as movie}
		<Card {movie} />
	{/each}
</div>

<style>
	.cards {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-wrap: wrap;
		gap: 20px;
	}
</style>
