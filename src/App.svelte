<script>
	const gridSize = 11;
	const colours = ['darkblue', 'blue', 'cornflowerblue', 'lightblue'];
	const cells = Array(gridSize * gridSize).fill(0).map((_, index) => ({
		text: `Cell ${index + 1}`,
		colour: colours[(index % colours.length)]
	}));
	const gridInstructions = `
		grid-template-columns: repeat(${gridSize}, ${100/gridSize}vw);
		grid-template-rows: repeat(${gridSize}, ${100/gridSize}vh);
	`;

</script>

<main class="gridContainer" style="{gridInstructions}">
	{#each cells as cell}
		<div style="background-color: {cell.colour}">{cell.text}</div>
	{/each}
</main>

<style>
	.gridContainer {
		display: grid;
		width: 100vw;
		height: 100vh;
	}

	div {
		color: white;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>