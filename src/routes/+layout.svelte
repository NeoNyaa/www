<script lang="ts">
	import './layout.css';
	import favicon from '$lib/assets/img/favicon.svg';

	let { children } = $props();
	const underDev = true;
</script>

<svelte:head>
	<link
		rel="icon"
		href={favicon} />
</svelte:head>

<!-- Navbar -->
<div class="navbar sticky top-0 bg-base-200 shadow-sm">
	<div class="flex-none">
		<a href="/"
			><img
				class="mx-4 size-10"
				alt="Site favicon"
				src={favicon} /></a>
	</div>
	<div class="flex-1">
		<ul class="menu menu-horizontal px-1">
			<li><a href="/Links">Links</a></li>
			<li>
				<details>
					<summary>Utils</summary>
					<ul class="w-max rounded-t-none bg-base-200 p-2">
						<li><a href=".">Optimal Superpairs Meter</a></li>
					</ul>
				</details>
			</li>
		</ul>
	</div>
	<!-- Under Development Notice -->
	{#if underDev}
		<div
			role="alert"
			class="mr-4 alert w-max py-2 alert-error dark:alert-soft">
			<span>IN DEVELOPMENT</span>
		</div>
	{/if}
</div>

{@render children()}

<!-- Back to top button -->
<!-- <a href="#top">
	<div class="fab">
		<button class="btn btn-circle btn-md btn-primary"
		><svg
		xmlns="http://www.w3.org/2000/svg"
		width="32"
		height="32"
		fill="currentColor"
		class="bi bi-arrow-up-short"
		viewBox="0 0 16 16">
		<path
		fill-rule="evenodd"
		d="M8 12a.5.5 0 0 0 .5-.5V5.707l2.146 2.147a.5.5 0 0 0 .708-.708l-3-3a.5.5 0 0 0-.708 0l-3 3a.5.5 0 1 0 .708.708L7.5 5.707V11.5a.5.5 0 0 0 .5.5" />
		</svg></button>
		</div>
		</a> -->

<!-- Footer -->
<!-- <footer
	class="footer-center absolute bottom-0 footer bg-base-200 p-4 text-base-content sm:footer-horizontal">
	<aside>
		<p>Made with SvelteKit/TailwindCSS/DaisyUI + and an insane amount of headaches.</p>
	</aside>
</footer> -->
