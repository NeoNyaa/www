<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/img/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

<nav
	class="sticky top-0 flex flex-row items-center space-x-4 border-b-2 border-black/10 bg-background-100 p-2 text-accent-700 dark:border-white/10"
>
	<a href="/" aria-label="home"><img class="size-10" alt="Site favicon" src={favicon} /></a>
	<a href="/links">Links</a>
	<a href="/utils">Utils</a>
	<pre
		class="ml-auto w-fit rounded-md border-2 border-red-500/50 bg-red-500/25 p-1 text-red-500 select-none"> IN DEVELOPMENT </pre>
</nav>

{@render children()}
