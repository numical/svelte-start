<script>
	const numCols = 5;
	const numRows = 5;
	const colours = ['darkblue', 'blue', 'cornflowerblue', 'lightblue'];
	const cells = Array(numCols * numCols).fill(0).map((_, index) => ({
		text: `Cell ${index + 1}`,
		colour: colours[(index % colours.length)]
	}));
	const gridInstructions = `
		grid-template-columns: repeat(${numCols}, ${100/numCols}vw);
		grid-template-rows: repeat(${numRows}, calc((100vh - 2rem - 10px)/${numRows}));
	`;

</script>

<main>
	<div class="title">
		{`A ${numCols} x ${numRows} grid`}
	</div>
	<div class="gridContainer" style="{gridInstructions}">
		{#each cells as cell}
			<div class="gridCell" style="background-color: {cell.colour}">{cell.text}</div>
		{/each}
	</div>
</main>

<style>
	.title {
		font-size: 2rem;
		text-align: center;
		height: calc(2rem + 10px);
	}
	.gridContainer {
		display: grid;
		width: 100vw;
	}

	.gridCell {
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