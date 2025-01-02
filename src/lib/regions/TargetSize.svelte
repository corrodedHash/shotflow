<script>
    import SkySelect from "../components/SkySelect.svelte";

    const sizeClasses = [
        {
            id: "extra_tiny",
            display: "Kleiner als winzig",
            extraText: "Pro Größenklasse +2",
            mod: +10,
        },
        {
            id: "tiny",
            display: "Winzig",
            extraText: "Münze, Drachenauge, Maus, Kröte",
            mod: +8,
        },
        {
            id: "very_small",
            display: "Sehr klein",
            extraText: "Schlange, Fasan, Katze, Rabe",
            mod: +6,
        },
        {
            id: "small",
            display: "Klein",
            extraText: "Wolf, Reh, Schaf",
            mod: +4,
        },
        {
            id: "medium",
            display: "Mittel",
            extraText: "Mensch, Elf, Ork, Goblin, Zwerg",
            mod: +2,
        },
        {
            id: "big",
            display: "Groß",
            extraText: "Pferd, Steppenrind, Oger, Troll",
            mod: 0,
        },
        {
            id: "very_big",
            display: "Sehr groß",
            extraText: "Scheunentor, Drache, Elefant, Riese",
            mod: -2,
        },
        {
            id: "extra_big",
            display: "Größer als sehr groß",
            extraText: "wie sehr groß",
            mod: -2,
        },
    ];
    let selectedTargetSize = $state();

    let { onModChange } = $props();

    $effect(() => {
        onModChange(selectedTargetSize?.mod);
    });
</script>

<div>
    {selectedTargetSize?.mod}
    <SkySelect options={sizeClasses} bind:value={selectedTargetSize} />
</div>
