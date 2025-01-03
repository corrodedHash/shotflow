<script>
    import ModBox from "../components/ModBox.svelte";
    import SkySelect from "../components/SkySelect.svelte";

    let { onModChange } = $props();

    const windStrengthClasses = [
        { id: "none", display: "Kein Wind", mod: 0 },
        { id: "normal", display: "Böiger Seitenwind", mod: +4 },
        { id: "strong", display: "Starker, böiger Seitenwind", mod: +8 },
    ];
    let selectedWindStrength = $state();

    $effect(() => {
        onModChange(selectedWindStrength?.mod);
    });
</script>

{#snippet modprops()}
    <SkySelect
        options={windStrengthClasses}
        bind:value={selectedWindStrength}
    />
{/snippet}

<ModBox result={selectedWindStrength?.mod} {modprops} />
