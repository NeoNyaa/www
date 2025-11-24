<script lang="ts">
	import { page } from '$app/state';
</script>

<div class="flex flex-col items-center text-text-900 mt-20">
	<div class="text-center text-5xl font-black">
		<pre>ERROR: {page.status}</pre>
	</div>
	<pre class="text-2xl">{page.error?.message}</pre>
</div>
