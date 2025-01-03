<script>
    import ModBox from "../components/ModBox.svelte";
    import SkyCheck from "../components/SkyCheck.svelte";

    /**
     * @typedef Props
     * @property {"none"| "sharpshooter"| "master"} skilllevel
     * @property {boolean} is_shooting
     */

    /** @type {Props} */
    let { skilllevel, onModChange, is_shooting } = $props();

    let speed_shot = $state(false);
    let second_shot = $state(false);
    let aiming = $state(0);

    let speed_shot_mods = {
        none: 2,
        sharpshooter: 1,
        master: 0,
    };

    let mod_change = $derived.by(() => {
        let mod_change = 0;
        if (speed_shot) {
            mod_change += speed_shot_mods[skilllevel];
        }
        if (second_shot) {
            mod_change += is_shooting ? 4 : 2;
        }
        const aiming_factor = skilllevel === "none" ? 2 : 1;
        mod_change += aiming_factor * aiming;
        return mod_change;
    });
    $effect(() => {
        onModChange(mod_change);
    });
</script>

{#snippet modprops()}
    <SkyCheck bind:checked={speed_shot} label="Schnellschuss" />
    <SkyCheck bind:checked={second_shot} label="Zweiter Schuss in Kampfrunde" />
    <div>
        Aktionen Zielen
        <input type="number" bind:value={aiming} />
    </div>
{/snippet}
<ModBox result={mod_change} {modprops} />
