<script>
	import { cart, total } from '$lib/stores'

	const minusItem = (product) => {
		for (let item of $cart) {
			if (item.id === product.id) {
				if (product.quantity > 1) {
					product.quantity -= 1
					$cart = $cart
				} else {
					$cart = $cart.filter((cartItem) => cartItem != product)
				}
				return
			}
		}
	}
	const plusItem = (product) => {
		for (let item of $cart) {
			if (item.id === product.id) {
				product.quantity += 1
				$cart = $cart
				return
			}
		}
	}

	$total = $cart.reduce((sum, item) => sum + item.price * item.quantity, 0)
</script>

<div class="cart-list">
	{#each $cart as item}
		{#if item.quantity > 0}
			<div class="cart-item">
				<img width="50" height="50" src="{item.image}" alt="{item.name}" />
				<span>{item.name}</span>
				<div class="cart-quantity">
					{item.quantity}
					<button on:click="{() => plusItem(item)}">+</button>
					<button on:click="{() => minusItem(item)}">-</button>
				</div>
				<p>${item.price * item.quantity}</p>
			</div>
		{/if}
	{/each}
	<div class="total">
		<h4>Total: $ {$total}</h4>
	</div>
</div>

<style>
	.cart-item {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
	}
	.total {
		text-align: right;
	}
	.cart-list {
		padding: 10px;
		margin-bottom: 1rem;
	}
	.cart-quantity {
		display: flex;
		justify-content: center;
		align-items: center;
	}
	.cart-quantity > button {
		margin-left: 0.3rem;
	}
	p {
		margin: 0;
		display: flex;
		justify-content: center;
		align-items: center;
	}
	span {
		display: flex;
		justify-content: center;
		align-items: center;
	}
	h4 {
		margin: 0;
	}
</style>
