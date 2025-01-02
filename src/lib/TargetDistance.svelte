<script>
    import SkySelect from "./components/SkySelect.svelte";

    let { mod_change = $bindable(0) } = $props();

    const distanceClasses = [
        { id: "sehr_nah", display: "Sehr nah", mod: -2 },
        { id: "nah", display: "Nah", mod: 0 },
        { id: "mittel", display: "Mittel", mod: +4 },
        { id: "weit", display: "Weit", mod: +8 },
        { id: "extrem_weit", display: "Extrem weit", mod: +12 },
    ];
    let selectedTargetDistance = $state();

    $effect(() => {
        mod_change = selectedTargetDistance?.mod;
    });
</script>

<div>
    <SkySelect options={distanceClasses} bind:value={selectedTargetDistance} />
    {selectedTargetDistance?.mod}
</div>
