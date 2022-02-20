<script>
	import { address, cart, modalActive, total } from '$lib/stores'
	import { goto } from '$app/navigation'

	function close() {
		$modalActive = false
		$cart = []
		$address = {
			name: '',
			email: '',
			phone: '',
			street: '',
			city: '',
			state: '',
			pin: ''
		}
		goto('/')
	}
</script>

{#if $modalActive}
	<div class="modal-background" on:click="{close}"></div>

	<div class="modal" role="dialog" aria-modal="true">
		<slot name="header" />
		{#each $cart as item}
			<div class="text">
				<p><b>{item.name}</b></p>
				<p>quantity: {item.quantity}</p>
			</div>
		{/each}
		<p><b>Total: {$total}</b></p>
		<!-- svelte-ignore a11y-autofocus -->
		<button autofocus on:click="{close}">close modal</button>
	</div>
{/if}

<style>
	.modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background-color: rgba(0, 0, 0, 0.3);
	}
	.modal {
		position: absolute;
		left: 50%;
		top: 50%;
		width: calc(100vw - 4em);
		max-width: 32em;
		max-height: calc(100vh- 4em);
		overflow: auto;
		transform: translate(-50%, -50%);
		padding: 1em;
		border-radius: 0.2em;
		background-color: white;
	}
	button {
		background-color: rgba(240, 128, 128, 0.7);
		border: none;
		border-radius: 5px;
		padding: 0.5rem;
		color: white;
		cursor: pointer;
		transition: 0.3s;
	}
	button:hover {
		background-color: rgba(240, 128, 128, 1);
	}
	.text {
		display: flex;
	}
	.text p {
		margin-right: 1rem;
	}
</style>
