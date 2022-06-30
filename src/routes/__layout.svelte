<script>
	import Footer from '../components/Footer.svelte';
	import Nav from '../components/Nav.svelte';
	import '../global.css';
</script>

<svelte:head>
	<title>Movie</title>
</svelte:head>

<Nav />
<slot />
<Footer />
