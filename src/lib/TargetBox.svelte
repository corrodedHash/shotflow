<script>
    import TargetDistance from "./regions/TargetDistance.svelte";
    import TargetSize from "./regions/TargetSize.svelte";
    import TargetBody from "./regions/TargetBody.svelte";
    import ViewSituation from "./regions/ViewSituation.svelte";
    import WindBox from "./regions/WindBox.svelte";
    import CoverBox from "./regions/CoverBox.svelte";
    import TargetMovement from "./regions/TargetMovement.svelte";

    let { mod_change = $bindable(0) } = $props();
    let body_mod = $state(0);
    let movement_mod = $state(0);
    let cover_mod = $state(0);
    let size_mod = $state(0);
    let wind_mod = $state(0);
    let view_mod = $state(0);
    let distance_mod = $state(0);

    $effect(() => {
        mod_change =
            body_mod +
            movement_mod +
            cover_mod +
            size_mod +
            wind_mod +
            view_mod +
            distance_mod;
    });
</script>

<div>
    <TargetDistance bind:mod_change={distance_mod} />
    <ViewSituation bind:mod_change={view_mod} />
    <WindBox bind:mod_change={wind_mod} />
    <TargetSize bind:mod_change={size_mod} />
    <TargetBody skilllevel="none" bind:mod_change={body_mod} />
    <CoverBox bind:mod_change={cover_mod} />
    <TargetMovement bind:mod_change={movement_mod} />
</div>
