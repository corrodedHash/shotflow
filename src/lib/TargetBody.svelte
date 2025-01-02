<script>
    import SkySelect from "./components/SkySelect.svelte";
    import SkyToggle from "./components/SkyToggle.svelte";

    /**
     * @typedef Props
     * @property {"none"| "sharpshooter"| "master"} skilllevel Some documentation
     */

    /** @type {Props} */
    let { skilllevel } = $props();
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

    const factor_map = {
        none: 1,
        sharpshooter: 2 / 3,
        master: 1 / 2,
    };
    const display_map = {
        none: "Schütze",
        sharpshooter: "Scharfschütze",
        master: "Meisterschütze",
    };

    let is_human = $state(true);
</script>

<div>
    {selectedPart?.display} [{selectedPart?.mod}] * {display_map[skilllevel]} [{factor_map[
        skilllevel
    ]}] =
    {selectedPart?.mod * factor_map[skilllevel]}
</div>
<SkyToggle labelOn="Mensch" labelOff="Vieh" bind:checked={is_human} />
{#if is_human}
    <SkySelect options={human_body_parts} bind:value={selectedPart} />
{:else}
    <SkySelect options={animal_body_parts} bind:value={selectedPart} />
{/if}
