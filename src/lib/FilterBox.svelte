<script>
	import { createEventDispatcher } from "svelte";

	const dispatch = createEventDispatcher();

	let selectedCategories = [];

	$: dispatch("update", selectedCategories);

	export let products;

	let categories = [];
	for (let i = 0; i < products.length; i++) {
		const item = products[i];
		if (!categories.includes(item.category)) {
			categories.push(item.category);
		}
	}
</script>

<div class="container">
	<div class="section-title">Category</div>
	{#each categories as cat}
		<label for={cat}>
			<input
				type="checkbox"
				name={cat}
				id={cat}
				value={cat}
				bind:group={selectedCategories}
			/>
			{cat}
		</label>
	{/each}
</div>

<style>
	.container {
		display: flex;
		flex-direction: column;
		width: max-content;
		border: 1px solid rgb(203, 203, 203);
		border-radius: 5px;
		padding: 5px;
	}
	.section-title {
		font-weight: bold;
		text-align: center;
	}
</style>
