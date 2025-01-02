<script>
    import SkySelect from "../components/SkySelect.svelte";
    import SkyCheck from "../components/SkyCheck.svelte";

    let { onModChange } = $props();

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

    $effect(() => {
        let mod_change =
            selectedAerosol?.sizemod * -2 +
            selectedLighting?.sizemod * -2 +
            (selectedInvisibility ? 8 : 0);
        mod_change = Math.min(8, mod_change);
        onModChange(mod_change);
    });
</script>

<div>
    {selectedAerosol?.sizemod * -2}
    {selectedLighting?.sizemod * -2}
    {selectedInvisibility}
    <SkySelect options={aerosolClasses} bind:value={selectedAerosol} />
    <SkySelect options={lightingClasses} bind:value={selectedLighting} />
    <SkyCheck bind:checked={selectedInvisibility} label="Unsichtbar" />
</div>
