<script>
    import SkySelect from "../components/SkySelect.svelte";

    let { onModChange } = $props();

    const distanceClasses = [
        { id: "sehr_nah", display: "Sehr nah", mod: -2 },
        { id: "nah", display: "Nah", mod: 0 },
        { id: "mittel", display: "Mittel", mod: +4 },
        { id: "weit", display: "Weit", mod: +8 },
        { id: "extrem_weit", display: "Extrem weit", mod: +12 },
    ];
    let selectedTargetDistance = $state();

    $effect(() => {
        onModChange(selectedTargetDistance?.mod);
    });
</script>

<div>
    {selectedTargetDistance?.mod}
    <SkySelect options={distanceClasses} bind:value={selectedTargetDistance} />
</div>
