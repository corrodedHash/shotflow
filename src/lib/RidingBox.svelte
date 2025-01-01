<script>
    import SkyCheck from "./components/SkyCheck.svelte";
    import SkySelect from "./components/SkySelect.svelte";

    const horseSpeedClass = [
        { id: "none", display: "Kein Reittier", mod: 0 },
        { id: "standing", display: "Von stehendem Reittier", mod: +2 },
        { id: "walk", display: "Von Reittier im Schritt", mod: +4 },
        { id: "gallop", display: "Von galoppierendem Reittier", mod: +8 },
    ];
    let unpreparedHorse = $state(false);
    let selectedHorseSpeed = $state();
</script>

<div>
    {selectedHorseSpeed?.mod}
    <SkySelect options={horseSpeedClass} bind:value={selectedHorseSpeed} />
    <SkyCheck
        bind:checked={unpreparedHorse}
        label="Ohne Sattel und Steigbügel"
    />
</div>
