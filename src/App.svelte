<script>
	import Home from "./pages/Home.svelte";
	import Product from "./pages/Product.svelte";
	import { Router, Link, Route } from "svelte-routing";
	import { products } from "./assets/products.json";

	export let url = "/";
</script>

<Router {url}>
	<Link to="/">Home</Link>
	<Link to="/product/3">Product</Link>
	<div>
		<Route path="/product/:id" let:params>
			<Product product={products.find((item) => item.id == params.id)} />
		</Route>
		<Route path="/">
			<Home {products} />
		</Route>
	</div>
</Router>
