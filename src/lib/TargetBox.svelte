<script>
    const distanceClasses = [
        { id: "sehr_nah", display: "Sehr nah", mod: -2 },
        { id: "nah", display: "Nah", mod: 0 },
        { id: "mittel", display: "Mittel", mod: +4 },
        { id: "weit", display: "Weit", mod: +8 },
        { id: "extrem_weit", display: "Extrem weit", mod: +12 },
    ];
    const shotDirection = [
        { id: "shot_straight", display: "Gerade", mod: 0 },
        { id: "shot_down", display: "Schuss/Wurf nach unten", mod: +2 },
        { id: "shot_up", display: "Schuss nach oben", mod: +4 },
        { id: "throw_up", display: "Wurf nach oben", mod: +8 },
    ];
    const sizeClass = [
        {
            id: "kleiner als winzig",
            display: "Kleiner als winzig",
            extraText: "Pro Größenklasse +2",
            mod: +10,
        },
        {
            id: "winzig",
            display: "Winzig",
            extraText: "Münze, Drachenauge, Maus, Kröte",
            mod: +8,
        },
        {
            id: "sehr klein",
            display: "Sehr klein",
            extraText: "Schlange, Fasan, Katze, Rabe",
            mod: +6,
        },
        {
            id: "klein",
            display: "Klein",
            extraText: "Wolf, Reh, Schaf",
            mod: +4,
        },
        {
            id: "mittel",
            display: "Mittel",
            extraText: "Mensch, Elf, Ork, Goblin, Zwerg",
            mod: +2,
        },
        {
            id: "groß",
            display: "Groß",
            extraText: "Pferd, Steppenrind, Oger, Troll",
            mod: 0,
        },
        {
            id: "sehr groß",
            display: "Sehr groß",
            extraText: "Scheunentor, Drache, Elefant, Riese",
            mod: -2,
        },
        {
            id: "größer als sehr groß",
            display: "Größer als sehr groß",
            extraText: "wie sehr groß",
            mod: -2,
        },
    ];
</script>

<div>
    <select bind:value={targetSize}>
        <option value="">{option.text}</option>
    </select>
</div>
