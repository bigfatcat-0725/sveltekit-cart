<script>
	import Address from '$lib/components/Address.svelte'
	import CartLength from '$lib/components/CartLength.svelte'
	import Modal from '$lib/components/Modal.svelte'
</script>

<Address />

<Modal>
	<h2 slot="header">Your order has been received</h2>
</Modal>

<style>
	h2 {
		color: lightcoral;
	}
</style>
