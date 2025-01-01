<script>
    import SkySelect from "./components/SkySelect.svelte";

    const human_body_parts = [
        { id: "head", display: "Kopf", mod: +10 },
        { id: "chest", display: "Brust", mod: +6 },
        { id: "arm", display: "Arm", mod: +10 },
        { id: "leg", display: "Beine", mod: +8 },
        { id: "belly", display: "Bauch", mod: +6 },
        { id: "hand", display: "Hand/Fuß", mod: +16 },
        { id: "eye", display: "Auge/Herz", mod: +20 },
    ];
    const animal_body_parts = [
        { id: "rump", display: "Rumpf", mod: +4 },
        { id: "leg", display: "Beine", mod: +10 },
        { id: "weakspot", display: "Verwundbare Stelle", mod: +12 },
        { id: "head", display: "Kopf", mod: +16 },
        { id: "small_tail", display: "Kleiner Schwanz", mod: +16 },
        { id: "big_tail", display: "Großer Schwanz", mod: +8 },
        { id: "sensory", display: "Sinnesorgane", mod: +16 },
    ];
    let selectedPart = $state();
</script>
{selectedPart?.display}
{selectedPart?.mod}
<SkySelect options={human_body_parts} bind:value={selectedPart} />
<SkySelect options={animal_body_parts} bind:value={selectedPart} />