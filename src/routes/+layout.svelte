<script lang="ts">
	import favicon from '/src/assets/img/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav>
	<a href="/" aria-label="home"><img src="{favicon}" alt="Site favicon" /></a>
	<a href="/">Home</a>
	<a href="/links">Links</a>
	<a href="/utils/hypixel-skyblock/Experiment-Book-Meter">Experiment-Book-Meter</a>
</nav>

{@render children()}
