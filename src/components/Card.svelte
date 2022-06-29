<script>
	export let movie;
	const imgUrl = 'http://image.tmdb.org/t/p/w500';
</script>

<a href={`/movie/${movie.id}`}>
	<img src={imgUrl + movie.poster_path} alt={movie.title} />
</a>

<style>
	img {
		width: 200px;
		border-radius: 10px;
	}
</style>
