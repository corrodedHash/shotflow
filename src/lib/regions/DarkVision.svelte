<script>
    import SkyCheck from "../components/SkyCheck.svelte";
    import SkyMultiToggle from "../components/SkyMultiToggle.svelte";

    let { onDarkvisionChange } = $props();

    const darkvision_options = [
        { id: "none", display: "Normal" },
        { id: "twilight", display: "Dämmerungssicht" },
        { id: "night", display: "Nachtsicht" },
    ];
    let selected_darkvision = $state(0);

    $effect(() => {
        onDarkvisionChange(darkvision_options[selected_darkvision].id);
    });
</script>

<SkyMultiToggle
    options={darkvision_options}
    bind:selected={selected_darkvision}
/>
