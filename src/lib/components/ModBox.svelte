<script>
    let { modprops, result } = $props();
</script>

<div class="modbox">
    <div class="modprops">
        {@render modprops()}
    </div>
    <div class="modresult">
        <span>{result}</span>
    </div>
</div>

<style>
    .modbox {
        display: flex;
        flex-direction: row;
        margin: 10px;
        padding: 4px;
        background-color: lightblue;
        --radius: 20px;
        border-radius: var(--radius);
    }

    /* .modtitle {
    } */

    .modprops {
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: center;
        flex-grow: 1;
    }

    .modresult {
        width: 100px;
        background-color: lightgreen;
        border-radius: 0 var(--radius) var(--radius) 0;
        margin: 4px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>
