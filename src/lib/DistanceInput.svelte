<script>
    let { distance = $bindable() } = $props();
</script>

<input type="number" bind:value={distance} />
