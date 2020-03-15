<script>
	export let name;
</script>

<main>
	<div class="one">Div 1</div>
	<div class="two">Div 2</div>
	<div class="three">Div 3</div>
	<div class="four">Div 4</div>
</main>

<style>
	main {
		display: grid;
		width: 100vw;
		height: 100vh;
		grid-template-columns: repeat(2, 50vmax);
		grid-template-rows: repeat(2, 50vmin);
	}

	div {
		color: white;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	.one {
		background-color: darkblue;
	}
	.two {
		background-color: blue;
	}
	.three {
		background-color: cornflowerblue;
	}
	.four {
		background-color: lightblue;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>