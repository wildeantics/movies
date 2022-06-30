<script>
	import FaGithub from 'svelte-icons/fa/FaGithub.svelte';
	import FaLinkedin from 'svelte-icons/fa/FaLinkedin.svelte';
	import FaGlobeAsia from 'svelte-icons/fa/FaGlobeAsia.svelte';
</script>

<footer>
	<div class="left">
		<span>Created by Morgan Wilde&copy;</span>
		<span>With use of Svelte and The Movie Database API</span>
	</div>
	<div class="right">
		<a href="https://github.com/wildeantics">
			<FaGithub />
		</a>
		<a href="https://www.linkedin.com/in/morganwilde/"><FaLinkedin /></a>
		<a href="https://wilde.mx/"><FaGlobeAsia /></a>
	</div>
</footer>

<style>
	footer {
		margin: 100px 10% 0 10%;
		display: flex;
		align-items: center;
		justify-content: space-between;
		color: #a5a5a5;
	}
	.left {
		display: flex;
		flex-direction: column;
	}
	.right {
		display: flex;
	}
	a {
		width: 40px;
		width: 40px;
		margin-right: 15px;
		color: #a5a5a5;
	}
</style>
