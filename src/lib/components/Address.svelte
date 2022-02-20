<script>
	import { address, modalActive } from '$lib/stores'
	import Cart from './Cart.svelte'

	const checkOut = () => {
		$modalActive = true
	}
</script>

<div class="shipping-address">
	<div>
		<p>Name</p>
		<input bind:value="{$address.name}" autocomplete="new-password" />
		<p>Email</p>
		<input bind:value="{$address.email}" autocomplete="new-password" />
		<p>Phone</p>
		<input bind:value="{$address.phone}" autocomplete="new-password" />
		<p>Address</p>
		<textarea bind:value="{$address.street}" cols="24" rows="6" autocomplete="new-password"
		></textarea>
		<p>City</p>
		<input bind:value="{$address.city}" autocomplete="new-password" />
		<p>State</p>
		<input bind:value="{$address.state}" autocomplete="new-password" />
		<p>PIN</p>
		<input bind:value="{$address.pin}" autocomplete="new-password" />
	</div>

	<div class="current-address">
		<p>Name: {$address.name}</p>
		<p>Email: {$address.email}</p>
		<p>Phone: {$address.phone}</p>
		<p>Address: {$address.street}</p>
		<p>City: {$address.city}</p>
		<p>State: {$address.state}</p>
		<p>PIN: {$address.pin}</p>
		<Cart />
		<div>
			<button class="checkout" on:click="{checkOut}">Checkout</button>
		</div>
	</div>
</div>

<style>
	.shipping-address {
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-gap: 1em;
	}
	.current-address {
		padding: 2em;
		border: 2px dashed green;
		position: relative;
	}
	.checkout {
		background-color: rgba(240, 128, 128, 0.7);
		border: none;
		border-radius: 5px;
		padding: 1rem;
		color: white;
		cursor: pointer;
		transition: 0.3s;
		position: absolute;
		left: 50%;
		bottom: 5%;
		transform: translate(-50%, 0);
	}
	.checkout:hover {
		background-color: rgba(240, 128, 128, 1);
	}
</style>
