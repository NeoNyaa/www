<script lang="ts">
	import { page } from '$app/state';
</script>

<div class="hero min-h-screen bg-base-200">
	<div class="hero-content">
		<div class="max-w-md text-center">
			<h1 class="text-5xl font-bold">Oh Nyoo &gt.&lt</h1>
			<p class="py-6">
				<b>Error Code:</b>
				{page.status}<br />
				<b>Error Message:</b>
				{page.error?.message}
			</p>
			<a
				href="/"
				class="btn btn-primary">Go back home?</a>
		</div>
	</div>
</div>
