<script>
    import ModBox from "../components/ModBox.svelte";
    import SkySelect from "../components/SkySelect.svelte";

    let { onModChange } = $props();

    const movementClass = [
        { id: "mounted", display: "Fest montiertes Ziel", sizemod: +2 },
        { id: "still", display: "Stillstehendes Ziel", sizemod: +1 },
        { id: "slow", display: "Leichte Bewegung", sizemod: +0 },
        { id: "fast", display: "Schnelle Bewegung", sizemod: -1 },
        { id: "very_fast", display: "Sehr schnelle Bewegung", sizemod: -2 },
    ];
    let fighting_crowd_hand = $state(0);
    let fighting_crowd_sword = $state(0);
    let selectedMovement = $state();
    let mod_change = $derived.by(() => {
        let mod_change;
        if (fighting_crowd_hand > 0 || fighting_crowd_sword > 0) {
            mod_change = fighting_crowd_hand * 3 + fighting_crowd_sword * 2;
        } else {
            mod_change = selectedMovement?.sizemod * -2;
        }
        return mod_change;
    });
    $effect(() => {
        onModChange(mod_change);
    });
</script>

{#snippet modprops()}
    <SkySelect options={movementClass} bind:value={selectedMovement} />
    <div>
        Handgemenge ({fighting_crowd_hand * 3})
        <input type="number" bind:value={fighting_crowd_hand} />
    </div>
    <div>
        Schwert-/Speerkampfgemenge ({fighting_crowd_sword * 2})
        <input type="number" bind:value={fighting_crowd_sword} />
    </div>
{/snippet}

<ModBox result={mod_change} {modprops} />
