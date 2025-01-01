<script>
    let {
        value = $bindable(),
        options,
        key = "id",
        display_key = "display",
    } = $props();
    let selectedValue = $state();
    $effect(() => {
        if (selectedValue === undefined) {
            value = undefined;
        }
        value = options.find((v) => v[key] === selectedValue);
    });
</script>

<select bind:value={selectedValue}>
    {#each options as t}
        <option value={t[key]}>{t[display_key]}</option>
    {/each}
</select>
