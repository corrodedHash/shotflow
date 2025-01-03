<script>
    import ModBox from "../components/ModBox.svelte";
    import SkyCheck from "../components/SkyCheck.svelte";
    import SkySelect from "../components/SkySelect.svelte";

    let { onModChange, is_shooting } = $props();
    const horseSpeedClass = [
        { id: "none", display: "Kein Reittier", mod: 0 },
        { id: "standing", display: "Von stehendem Reittier", mod: +2 },
        { id: "walk", display: "Von Reittier im Schritt", mod: +4 },
        { id: "gallop", display: "Von galoppierendem Reittier", mod: +8 },
    ];
    let unpreparedHorse = $state(false);
    let selectedHorseSpeed = $state();
    let mod_change = $derived.by(() => {
        const horseMod = unpreparedHorse ? +4 : 0;
        let mod_change = selectedHorseSpeed?.mod + horseMod;
        if (!is_shooting) {
            mod_change = Math.round(mod_change / 2);
        }
        return mod_change;
    });
    $effect(() => {
        onModChange(mod_change);
    });
</script>

{#snippet modprops()}
    <SkySelect options={horseSpeedClass} bind:value={selectedHorseSpeed} />
    <SkyCheck
        bind:checked={unpreparedHorse}
        label="Ohne Sattel und Steigbügel"
    />
{/snippet}
<ModBox {modprops} result={mod_change} />
