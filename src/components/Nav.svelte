<script>
	import { goto } from '$app/navigation';
	import { fly } from 'svelte/transition';
	let inputValue = '';

	function submitSearch() {
		goto('/search/' + inputValue);
	}
</script>

<nav>
	<a href="/" class="title">Movies</a>
	<form class="search" on:submit|preventDefault={submitSearch}>
		<input
			bind:value={inputValue}
			type="text"
			class="searchBox"
			placeholder="Search for movies..."
		/>
		{#if inputValue}
			<button
				class="searchButton"
				in:fly={{ x: -20, duration: 500 }}
				out:fly={{ x: -20, duration: 500 }}>Search</button
			>
		{/if}
	</form>
</nav>

<style>
	nav {
		height: 100px;
		display: flex;
		align-items: center;
		justify-content: space-around;
		background-color: transparent;
	}
	.title {
		font-size: 2.5em;
		text-decoration: none;
		text-transform: uppercase;
		font-weight: 700;
		color: white;
		text-shadow: -1px -1px 0 #000, 0 -1px 0 #000, 1px -1px 0 #000, 1px 0 0 #000, 1px 1px 0 #000,
			0 1px 0 #000, -1px 1px 0 #000, -1px 0 0 #000;
	}
	.search {
		width: 40vw;
		display: flex;
		position: relative;
		transition: all 0.3s ease-in-out;
	}
	.searchBox {
		flex: 2;
		padding: 0;
		border: none;
		height: 2em;
		border-radius: 12px;
		padding-left: 20px;
		background-color: rgba(48, 48, 48, 0.6);
		color: white;
	}
	.searchBox:focus {
		outline: none;
	}
	.searchButton {
		padding: 0;
		border: none;
		position: absolute;
		right: 0;
		height: 2em;
		border-radius: 12px;
		padding: 0 40px;
		background-color: rgb(75, 75, 75);
		color: white;
		cursor: pointer;
	}
</style>
