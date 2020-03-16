<script>
	import Cell from './Cell.svelte';
	import Graph from './Graph.svelte';
	const colours = ['darkblue', 'blue', 'cornflowerblue', 'lightblue'];
	let numCols = 5;
	let numRows = 5;
	$: cells = Array((numCols || 1) * (numRows || 1)).fill(0).map((_, index) => ({
		text: `Cell ${index + 1}`,
		colour: colours[(index % colours.length)]
	}));
	$: gridInstructions = `
		grid-template-columns: repeat(${numCols || 1}, ${100/(numCols || 1)}vw);
		grid-template-rows: repeat(${numRows || 1}, calc((100vh - 2rem - 10px)/${numRows || 1}));
	`;
</script>

<main>
	<div class="title">
		A
		<input type="number" min=1 max=99 bind:value={numCols} />
		x
		<input type="number" min=1 max=99 bind:value={numRows} />
		grid
	</div>
	<div class="gridContainer" style="{gridInstructions}">
		{#each cells as cell, i}
			{#if i > 0 && i % 7 === 0}
				<Graph />
			{:else}
				<Cell {cell} />
			{/if}

		{/each}
	</div>
</main>

<style>
	input[type=number] {
		text-align: center;
		width: 3rem;
		margin: 0;
		padding: 0;
		-moz-appearance: textfield;
	}
	input[type=number]::-webkit-inner-spin-button,
	input[type=number]::-webkit-outer-spin-button {
		-webkit-appearance: none;
		-moz-appearance: none;
		appearance: none;
		margin: 0;
	}
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