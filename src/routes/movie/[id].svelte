<script lang="ts" context="module">
	const API = import.meta.env.VITE_TMDB_API;
	const API_KEY = import.meta.env.VITE_API_KEY;
	export async function load({ fetch, params }: { fetch: any; params: any }) {
		const res = await fetch(`${API}/${params.id}?api_key=${API_KEY}`);
		const movie = await res.json();
		if (res.ok) {
			return { props: { movie } };
		}
	}
</script>

<script lang="ts">
	export let movie: any;
	const imgUrl = 'http://image.tmdb.org/t/p/original';
	import moment from 'moment';
	import { blur } from 'svelte/transition';

	import MdAccessTime from 'svelte-icons/md/MdAccessTime.svelte';
	import MdDateRange from 'svelte-icons/md/MdDateRange.svelte';
	import MdStar from 'svelte-icons/md/MdStar.svelte';
	import MdMonetizationOn from 'svelte-icons/md/MdMonetizationOn.svelte';
	import GiDominoMask from 'svelte-icons/gi/GiDominoMask.svelte';
	import FaImdb from 'svelte-icons/fa/FaImdb.svelte';
</script>

<div class="movie-details" in:blur={{ duration: 500 }} out:blur={{ duration: 300 }}>
	<img src={imgUrl + movie.backdrop_path} alt={movie.title} class="image" />
	<div class="text-container">
		<h1>{movie.title}</h1>
		<span class="tagline"><i>{movie.tagline}</i></span>
		<p>{movie.overview}</p>
	</div>
	<div class="movie-data">
		<div class="data-container">
			<div class="icon">
				<GiDominoMask />
			</div>
			{#each movie.genres as genre}
				<span>{genre.name}</span>
			{/each}
		</div>
		<div class="data-container">
			<div class="icon">
				<MdAccessTime />
			</div>
			<span>{movie.runtime} minutes</span>
		</div>
		<div class="data-container">
			<div class="icon">
				<MdDateRange />
			</div>
			<span>{moment(movie.release_date, 'YYYY-MM-DD').fromNow()}</span>
		</div>
		<div class="data-container">
			<div class="icon">
				<MdStar />
			</div>
			<span>{movie.vote_average}/10 from {movie.vote_count} ratings</span>
		</div>
		<div class="data-container">
			<div class="icon">
				<MdMonetizationOn />
			</div>
			<span>${movie.revenue.toLocaleString('en-US')}</span>
		</div>
		<a href={`https://www.imdb.com/title/${movie.imdb_id}`}>
			<div class="data-container">
				<div class="icon">
					<FaImdb />
				</div>
				<span>IMDB</span>
			</div>
		</a>
	</div>
</div>

<style>
	.movie-details {
		width: 100vw;
	}
	.image {
		width: 100%;
		position: absolute;
		top: 0;
		z-index: -1;
		-webkit-mask-image: -webkit-linear-gradient(
			270deg,
			rgba(0, 0, 0, 1) 0%,
			rgba(0, 0, 0, 1) 75%,
			rgba(0, 0, 0, 0) 100%
		);
		mask-image: linear-gradient(
			270deg,
			rgba(0, 0, 0, 1) 0%,
			rgba(0, 0, 0, 1) 75%,
			rgba(0, 0, 0, 0) 100%
		);
	}
	.text-container {
		margin: 40% 10% 0 10%;
	}
	h1 {
		margin-bottom: 0;
		font-size: 4em;
		text-transform: uppercase;
		line-height: 1;
	}
	.tagline {
		color: #c2c2c2;
		font-weight: 300;
		font-size: 1.3em;
		line-height: 1;
	}
	.movie-data {
		display: flex;
		align-items: flex-start;
		justify-content: center;
		margin: 0 10%;
		margin-top: 50px;
	}
	.movie-data > a {
		text-decoration: none;
		flex: 1;
	}
	.data-container {
		flex: 1;
		display: flex;
		align-items: center;
		flex-direction: column;
		color: white;
	}
	.data-container > span {
		text-align: center;
	}
	.icon {
		width: 60px !important;
	}
</style>
