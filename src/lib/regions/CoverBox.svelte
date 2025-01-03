<script>
    import ModBox from "../components/ModBox.svelte";
    import SkySelect from "../components/SkySelect.svelte";

    const coverClasses = [
        { id: "none", display: "Keine Deckung", sizemod: 0 },
        { id: "half", display: "Halbe Deckung", sizemod: -1 },
        { id: "three_quarter", display: "Dreiviertel Deckung", sizemod: -2 },
    ];
    let selectedCover = $state();

    let { onModChange } = $props();

    $effect(() => {
        onModChange(selectedCover?.sizemod * -2);
    });
</script>

{#snippet modprops()}
    <SkySelect options={coverClasses} bind:value={selectedCover} />
{/snippet}

<ModBox result={selectedCover?.sizemod * -2} {modprops} />
