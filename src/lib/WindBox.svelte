<script>
    import SkySelect from "./components/SkySelect.svelte";

    const windStrengthClasses = [
        { id: "none", display: "Kein Wind", mod: 0 },
        { id: "normal", display: "Böiger Seitenwind", mod: +4 },
        { id: "strong", display: "Starker, böiger Seitenwind", mod: +8 },
    ];
    let selectedWindStrength = $state();
</script>

<div>
    {selectedWindStrength?.mod}
    <SkySelect
        options={windStrengthClasses}
        bind:value={selectedWindStrength}
    />
</div>
