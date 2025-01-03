<script>
    import SkyCheck from "./components/SkyCheck.svelte";
    import SkyMultiToggle from "./components/SkyMultiToggle.svelte";

    let { onSkilllevelChange } = $props();
    let sharpshooter = $state(false);
    let mastershooter = $state(false);
    let skilllevel = $derived.by(() => {
        if (mastershooter) {
            return "master";
        } else if (sharpshooter) {
            return "sharpshooter";
        } else {
            return "none";
        }
    });
    let selected = $state(0);
    const options = [
        { id: "none", display: "Schütze" },
        { id: "sharpshooter", display: "Scharfschütze" },
        { id: "master", display: "Meisterschütze" },
    ];

    $effect(() => {
        onSkilllevelChange(options[selected].id);
    });
</script>

<SkyMultiToggle {options} bind:selected />
