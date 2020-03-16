<script>
    export let cell;
</script>

<div class="gridCell" style="background-color: {cell.colour}">{cell.text}</div>

<style>
    .gridCell {
        color: white;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>