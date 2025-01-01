<script>
    import SkyCheck from "./components/SkyCheck.svelte";

    let twilight_sight = $state(false);
    let nightvision = $state(false);
    let distance_sense = $state(false);
    let one_eyed = $state(false);
    let colorblind = $state(false);
    let shortsighted = $state(false);
    let nightblind = $state(false);

    let sharpshooter = $state(false);
    let mastershooter = $state(false);
</script>

<SkyCheck bind:checked={twilight_sight} label="Dämmerungssicht" />
<SkyCheck bind:checked={nightvision} label="Nachtsicht" />
<SkyCheck bind:checked={distance_sense} label="Entfernungssinn" />
<SkyCheck bind:checked={one_eyed} label="Einäugig" />
<SkyCheck bind:checked={colorblind} label="Farbenblind" />
<SkyCheck bind:checked={shortsighted} label="Kurzsichtig" />
<SkyCheck bind:checked={nightblind} label="Nachtblind" />
<SkyCheck bind:checked={sharpshooter} label="Scharfschütze" />
<SkyCheck bind:checked={mastershooter} label="Meiserschütze" />
