<script>
	import { cart, products } from '$lib/stores'
	import { goto } from '$app/navigation'

	const addToCart = (product) => {
		for (let item of $cart) {
			if (item.d === product.id) {
				product.quantity += 1
				$cart = $cart
				return
			}
		}
		$cart = [...$cart, product]
		const goCart = confirm('add complete! go cart?')
		if (goCart) goto('/cart')
	}
</script>

<div class="product-list">
	{#each $products as product}
		<div class="list">
			<div class="image" style="background-image: url({product.image});"></div>
			<h4>{product.name}</h4>
			<p>${product.price}</p>
			<button on:click="{() => addToCart(product)}">Add to cart</button>
		</div>
	{/each}
</div>

<style>
	.product-list {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		text-align: center;
	}
	.image {
		height: 150px;
		width: 150px;
		background-size: contain;
		background-position: center;
		background-repeat: no-repeat;
		margin: 0 auto;
	}
	.list {
		margin-bottom: 2rem;
	}
	button {
		background-color: rgba(240, 128, 128, 0.7);
		border: none;
		border-radius: 5px;
		padding: 0.3rem;
		color: white;
		cursor: pointer;
		transition: 0.3s;
	}
	button:hover {
		background-color: rgba(240, 128, 128, 1);
	}
</style>
