<script>
    import SkyCheck from "./components/SkyCheck.svelte";

    /**
     * @typedef Props
     * @property {"none"| "sharpshooter"| "master"} skilllevel Some documentation
     */

    /** @type {Props} */
    let { skilllevel } = $props();

    let speed_shot = $state(false);
    let second_shot = $state(false);
    let aiming = $state(0);
</script>

<div>
    <SkyCheck bind:checked={speed_shot} label="Schnellschuss" />
    <SkyCheck bind:checked={second_shot} label="Zweiter Schuss in Kampfrunde" />
    <div>
        Aktionen Zielen
        <input type="number" bind:value={aiming} />
    </div>
</div>
