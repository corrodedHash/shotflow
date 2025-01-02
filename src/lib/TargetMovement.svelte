<script>
    import SkySelect from "./components/SkySelect.svelte";

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
</script>

<div>
    {selectedMovement?.sizemod * -2}
    <SkySelect options={movementClass} bind:value={selectedMovement} />
    <div>
        Handgemenge ({fighting_crowd_hand * 2})
        <input type="number" bind:value={fighting_crowd_hand} />
    </div>
    <div>
        Schwert-/Speerkampfgemenge ({fighting_crowd_sword * 3})
        <input type="number" bind:value={fighting_crowd_sword} />
    </div>
</div>
