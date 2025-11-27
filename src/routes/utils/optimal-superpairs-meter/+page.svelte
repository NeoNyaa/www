<script lang="ts">
	import { onMount } from 'svelte';
	import { PRETTY_NAMES, hasPrettyName } from './prettyNames';
	import { millify } from 'millify';

	let bzData: any = null;
	let error: string | null = null;
	let loading: boolean = true;
	let valueDesc: any = [];

	onMount(async () => {
		try {
			const response = await fetch('https://api.hypixel.net/v2/skyblock/bazaar');
			if (!response.ok) {
				throw new Error(`Failed to fetch data from the hypixel API (HTTP: ${response.status})`);
			}
			bzData = await response.json();
			valueDesc = bzData.products
				? Object.values(bzData.products)
						.filter((p: any) => hasPrettyName(p.product_id))
						.sort((a: any, b: any) => b.quick_status.buyPrice - a.quick_status.buyPrice)
				: [];
		} catch (err: any) {
			error = err.message ?? 'Unknown Error';
		} finally {
			loading = false;
		}
	});
</script>

<div class="m-4 min-h-min overflow-x-auto">
	<table class="table table-sm md:table-lg">
		<thead>
			<tr>
				<th>Enchantment</th>
				<th>Value</th>
				<th>Sell Orders</th>
				<th>Buy Orders</th>
			</tr>
		</thead>
		<tbody>
			{#if loading}
				<tr>
					<td class="skeleton skeleton-text">Loading...</td>
					<td class="skeleton skeleton-text">Loading...</td>
					<td class="skeleton skeleton-text">Loading...</td>
					<td class="skeleton skeleton-text">Loading...</td>
				</tr>
			{:else if error}
				<tr>
					<td colspan="4">
						<div class="alert alert-error">
							<svg
								xmlns="http://www.w3.org/2000/svg"
								class="h-6 w-6 shrink-0 stroke-current"
								fill="none"
								viewBox="0 0 24 24">
								<path
									stroke-linecap="round"
									stroke-linejoin="round"
									stroke-width="2"
									d="M10 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2m7-2a9 9 0 11-18 0 9 9 0 0118 0z" />
							</svg>
							<span>Failed to load data: {error}</span>
						</div>
					</td>
				</tr>
			{:else}
				{#each valueDesc as item}
					<tr>
						<td>{PRETTY_NAMES[item.product_id]}</td>
						<td
							><pre>{millify(item.quick_status.buyPrice, {
									precision: 2,
									lowercase: true,
									units: ['', 'K', 'M', 'B', 'T', 'QU', 'QI']
								})}</pre></td>
						<td>{item.quick_status.sellOrders}</td>
						<td>{item.quick_status.buyOrders}</td>
					</tr>
				{/each}
			{/if}
		</tbody>
	</table>
</div>
