<script>
    import SkySelect from "./components/SkySelect.svelte";

    const coverClasses = [
        { id: "none", display: "Keine Deckung", sizemod: 0 },
        { id: "half", display: "Halbe Deckung", sizemod: -1 },
        { id: "three_quarter", display: "Dreiviertel Deckung", sizemod: -2 },
    ];
    let selectedCover = $state();
</script>

<div>
    {selectedCover?.sizemod * -2}
    <SkySelect options={coverClasses} bind:value={selectedCover} />
</div>
