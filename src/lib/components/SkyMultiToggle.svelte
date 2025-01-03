<script>
    let { options, selected = $bindable(0) } = $props();
</script>

<div onclick={() => (selected = (selected + 1) % options.length)}>
    {#each options as t, i}
        <span class={{ optionField: true, chosenOption: i === selected }}>
            {t.display}
        </span>
    {/each}
</div>

<style>
    .optionField {
        -webkit-user-select: none; /* Safari */
        -ms-user-select: none; /* IE 10 and IE 11 */
        user-select: none; /* Standard syntax */

        background-color: lightblue;
        padding-left: 3px;
        padding-right: 3px;
    }
    .optionField.chosenOption {
        background-color: darkblue;
        color: white;
    }
</style>
