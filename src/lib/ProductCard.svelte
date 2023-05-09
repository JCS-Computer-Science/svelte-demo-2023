<script>
	import FilledStars from "./FilledStars.svelte";

	export let product;
</script>

<div class="card">
	<div class="img-container">
		<img src={product.thumbnail} alt="" />
	</div>
	<div class="text-content">
		<h3>{product.title}</h3>
		<FilledStars score={product.rating} />

		<p class="description">
			{product.description.slice(0, 90)}{product.description.length > 90 ? "..." : ""}
		</p>

		<p class="price">${product.price.toFixed(2)}</p>
	</div>
</div>

<style>
	.img-container {
		width: 200px;
		height: 200px;
		overflow: hidden;
	}
	img {
		width: 200px;
		height: 200px;
		object-fit: cover;
		flex-shrink: 0;
		flex-grow: 0;
		transition: transform 0.3s ease;
	}
	img:hover {
		transform: scale(1.2);
	}
	.card {
		width: 200px;
		height: 350px;
		border-radius: 10px;
		display: flex;
		flex-direction: column;
		overflow: hidden;
		box-shadow: 1px 1px 4px 4px rgb(226, 226, 226);
		margin: 10px;
	}
	.text-content {
		padding: 5px;
		display: flex;

		flex-direction: column;
		overflow: hidden;
		text-overflow: ellipsis;
		flex-grow: 1;
	}
	.description {
		flex-grow: 1;
		overflow: hidden;
		/* text-overflow: ellipsis; */
	}

	* {
		margin: 0;
	}
	h3 {
		overflow: hidden;
		white-space: nowrap;
		text-overflow: ellipsis;
	}
</style>
