<script>
    const aerosolClasses = [
        { id: "normal", display: "Normal", sizemod: 0 },
        { id: "mist", display: "Dunst", sizemod: -1 },
        { id: "fog", display: "Nebel", sizemod: -2 },
    ];
    const lightingClasses = [
        { id: "normal", display: "Normal", sizemod: 0 },
        { id: "twilight", display: "Dämmerung", sizemod: -1 },
        { id: "moonlight", display: "Mondlicht", sizemod: -2 },
        { id: "starlight", display: "Sternenlicht", sizemod: -3 },
        { id: "darkness", display: "Finsternis", sizemod: -4 },
    ];
    const viewClasses = [
        { id: "invisible", display: "Unsichtbares Ziel", sizemod: -4 },
    ];
    let selectedAerosol = $state();
    let selectedLighting = $state();
    let selectedInvisibility = $state(false);
    let selectedAerosolMod = $derived.by(() => {
        const found_class = aerosolClasses.find(
            (v) => v.id === selectedAerosol,
        );
        if (found_class === undefined) {
            return 0;
        }
        return found_class.sizemod;
    });

    let selectedLightingMod = $derived.by(() => {
        const found_class = lightingClasses.find(
            (v) => v.id === selectedLighting,
        );
        if (found_class === undefined) {
            return 0;
        }
        return found_class.sizemod;
    });
</script>

<div>
    {selectedAerosolMod * -2}
    {selectedLightingMod * -2}
    <select bind:value={selectedAerosol}>
        {#each aerosolClasses as t}
            <option value={t.id}>{t.display}</option>
        {/each}
    </select>
    <select bind:value={selectedLighting}>
        {#each lightingClasses as t}
            <option value={t.id}>{t.display}</option>
        {/each}
    </select>
</div>
