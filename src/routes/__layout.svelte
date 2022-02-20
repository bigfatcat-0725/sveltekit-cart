<nav>
	<ul>
		<li><a href="/">Home</a></li>
		<li><a href="/cart">Cart</a></li>
	</ul>
	<span>Fruit Shop</span>
</nav>
<slot />

<style>
	nav {
		position: relative;
	}
	ul {
		display: flex;
		justify-content: space-between;
		padding: 0;
	}
	li {
		list-style: none;
	}
	a {
		display: block;
		padding: 1rem;
		text-decoration: none;
		color: white;
		font-weight: bold;
		background-color: rgba(240, 128, 128, 0.7);
		border-radius: 5px;
		transition: 0.3s;
	}
	a:hover {
		background-color: rgba(240, 128, 128, 1);
	}
	span {
		position: absolute;
		top: 50%;
		left: 50%;
		transform: translate(-50%, -50%);
		font-size: 2rem;
		font-weight: bold;
		color: lightsalmon;
	}
</style>
