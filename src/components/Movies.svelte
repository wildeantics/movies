<script lang="ts">
	export let movies: any;
	const imgUrl = 'http://image.tmdb.org/t/p/w500';
	import moviePoster from '../assets/Movie-Poster.png';
</script>

<div class="cards">
	{#each movies as movie}
		<a href={`/movie/${movie.id}`}>
			{#if movie.poster_path}
				<img src={imgUrl + movie.poster_path} alt={movie.title} />
			{:else}
				<img src={moviePoster} alt={movie.title} />
			{/if}
		</a>
	{/each}
	{#if movies.length === 0}
		<h1>Sorry there's not movies here</h1>
	{/if}
</div>

<style>
	.cards {
		display: flex;
		align-items: center;
		justify-content: center;
		flex-wrap: wrap;
		gap: 20px;
	}
	img {
		width: 200px;
		border-radius: 10px;
	}
</style>
