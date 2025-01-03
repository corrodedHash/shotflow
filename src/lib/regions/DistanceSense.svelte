<script>
    import SkyCheck from "../components/SkyCheck.svelte";
    import ModBox from "../components/ModBox.svelte";

    let { onModChange } = $props();

    let distance_sense = $state(false);
    let mod_change = $derived(distance_sense ? -2 : 0);
    $effect(() => {
        onModChange(mod_change);
    });
</script>

{#snippet modprops()}
    <SkyCheck bind:checked={distance_sense} label="Entfernungssinn" />
{/snippet}
<ModBox {modprops} result={mod_change} />
