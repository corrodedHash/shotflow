<script>
    const distanceClasses = [
        { id: "sehr_nah", display: "Sehr nah", mod: -2 },
        { id: "nah", display: "Nah", mod: 0 },
        { id: "mittel", display: "Mittel", mod: +4 },
        { id: "weit", display: "Weit", mod: +8 },
        { id: "extrem_weit", display: "Extrem weit", mod: +12 },
    ];
    let selectedTargetDistance = $state();
    let selectedTargetDistanceMod = $derived.by(() => {
        const found_class = distanceClasses.find(
            (v) => v.id === selectedTargetDistance,
        );
        if (found_class === undefined) {
            return 0;
        }
        return found_class.mod;
    });
</script>

<div>
    {selectedTargetDistanceMod}
    <select bind:value={selectedTargetDistance}>
        {#each distanceClasses as t}
            <option value={t.id}>{t.display}</option>
        {/each}
    </select>
</div>
