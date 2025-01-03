<script>
    import SkyCheck from "../components/SkyCheck.svelte";
    import ModBox from "../components/ModBox.svelte";

    let { onModChange, distance } = $props();

    let one_eyed = $state(false);
    let one_eyed_active = $derived(one_eyed && distance <= 10);
    let colorblind = $state(false);
    let colorblind_active = $derived(colorblind && distance >= 50);
    let shortsighted = $state(false);
    let shortsighted_active = $derived(shortsighted >= 100);

    let mod_change = $derived(
        (one_eyed_active ? 4 : 0) + (colorblind_active ? 4 : 0),
    );
    $effect(() => {
        onModChange(mod_change);
    });
</script>

{#snippet modprops()}
    <SkyCheck bind:checked={one_eyed} label="Einäugig" />
    <SkyCheck bind:checked={colorblind} label="Farbenblind" />
    <SkyCheck bind:checked={shortsighted} label="Kurzsichtig" />
{/snippet}

<ModBox result={mod_change} {modprops} />
