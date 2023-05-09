<script>
	import { products } from "./assets/products.json";
	import { scale } from "svelte/transition";
	import { flip } from "svelte/animate";
	import ProductCard from "./lib/ProductCard.svelte";
	import FilterBox from "./lib/FilterBox.svelte";

	let filteredProducts = products;

	function applyFilters(event) {
		let filterCategories = event.detail;
		filteredProducts = filterCategories.length
			? products.filter((item) => filterCategories.includes(item.category))
			: products;
	}

	// let filteredProducts = [];
	// for (let i = 0; i < products.length; i++) {
	// 	let item = products[i];
	// 	if (filterCategories.includes(item.category)) {
	// 		filteredProducts.push(item);
	// 	}
	// }
</script>

<div class="layout">
	<div class="sidebar">
		<FilterBox {products} on:update={applyFilters} />
	</div>
	<div class="product-list">
		{#each filteredProducts as item, i (item.id)}
			<div
				animate:flip={{ duration: 500, delay: 200 + i * 20 }}
				out:scale={{ duration: 250, delay: i * 20 }}
				in:scale={{ duration: 250, delay: 400 + i * 20 }}
			>
				<ProductCard product={item} />
			</div>
		{/each}
	</div>
</div>

<style>
	.layout {
		display: flex;
	}
	.sidebar {
		margin-top: 10px;
	}
	.product-list {
		display: flex;
		flex-wrap: wrap;
	}
</style>
