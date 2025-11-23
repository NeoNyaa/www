<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/img/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav class="bg-background-100">
	<a href="/" aria-label="home"><img src={favicon} alt="Site favicon" /></a>
	<a href="/links">Links</a>
	<a href="/utils/hypixel-skyblock/Experiment-Book-Meter">Experiment-Book-Meter</a>
	<pre class="text-red-500"> -[ IN DEVELOPMENT ]- </pre>
</nav>

{@render children()}
