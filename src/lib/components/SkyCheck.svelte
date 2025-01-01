<script>
    let { checked = $bindable(false), label = "" } = $props();
</script>

<div
    onclick={() => {
        checked = !checked;
    }}
>
    <input type="checkbox" bind:checked={checked} />
    <span>{label}</span>
</div>
