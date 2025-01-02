<script>
    import AdvantageBox from "./regions/AdvantageBox.svelte";
    import RidingBox from "./regions/RidingBox.svelte";
    import ShotConditions from "./regions/ShotConditions.svelte";

    let { is_shooting, onModChange } = $props();
    let character_info = $state();
    let character_mod = $state(0);
    let riding_mod = $state(0);
    let shot_mod = $state(0);
    $effect(() => {
        onModChange(riding_mod + shot_mod + character_mod);
    });
</script>

<AdvantageBox
    onCharacterChange={(e) => (character_info = e)}
    onModChange={(e) => (character_mod = e)}
/>
<RidingBox onModChange={(e) => (riding_mod = e)} />
<ShotConditions
    onModChange={(e) => (shot_mod = e)}
    skilllevel={character_info?.skilllevel}
    is_shooting
/>
