<script>
    import SkySelect from "../components/SkySelect.svelte";
    import SkyCheck from "../components/SkyCheck.svelte";
    import ModBox from "../components/ModBox.svelte";

    let { onModChange, darkvision, nightblind } = $props();

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
    let lightingMod = $derived.by(() => {
        const nightblindMod = nightblind ? 2 : 1;
        const rawMod = selectedLighting?.sizemod * -2 * nightblindMod;

        if (!rawMod) {
            return 0;
        }
        switch (darkvision) {
            case "none":
                return rawMod;

            case "twilight":
                return Math.round(rawMod * 0.5);

            case "night":
                if (rawMod <= 5) {
                    return 0;
                }
                return Math.max(rawMod - 5, 0);

            default:
                throw Error("Oops");
        }
    });
    let mod_change = $derived.by(() => {
        const mod_change =
            selectedAerosol?.sizemod * -2 +
            lightingMod +
            (selectedInvisibility ? 8 : 0);
        return Math.min(8, mod_change);
    });
    $effect(() => {
        onModChange(mod_change);
    });
</script>

{#snippet modprops()}
    <SkySelect options={aerosolClasses} bind:value={selectedAerosol} />
    <SkySelect options={lightingClasses} bind:value={selectedLighting} />
    <SkyCheck bind:checked={selectedInvisibility} label="Unsichtbar" />
{/snippet}
<ModBox result={mod_change} {modprops} />
