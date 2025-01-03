<script>
    import TargetDistance from "./regions/TargetDistance.svelte";
    import TargetSize from "./regions/TargetSize.svelte";
    import TargetBody from "./regions/TargetBody.svelte";
    import ViewSituation from "./regions/ViewSituation.svelte";
    import WindBox from "./regions/WindBox.svelte";
    import CoverBox from "./regions/CoverBox.svelte";
    import TargetMovement from "./regions/TargetMovement.svelte";

    let { onModChange, skilllevel } = $props();
    let body_mod = $state(0);
    let movement_mod = $state(0);
    let cover_mod = $state(0);
    let size_mod = $state(0);
    let wind_mod = $state(0);
    let distance_mod = $state(0);

    $effect(() => {
        // console.log(
        //     body_mod,
        //     movement_mod,
        //     cover_mod,
        //     size_mod,
        //     wind_mod,
        //     distance_mod,
        // );
        onModChange(
            body_mod +
                movement_mod +
                cover_mod +
                size_mod +
                wind_mod +
                distance_mod,
        );
    });
</script>

<div>
    <TargetDistance
        onModChange={(e) => {
            distance_mod = e;
        }}
    />
    <WindBox
        onModChange={(e) => {
            wind_mod = e;
        }}
    />
    <TargetSize
        onModChange={(e) => {
            size_mod = e;
        }}
    />
    <TargetBody
        {skilllevel}
        onModChange={(e) => {
            body_mod = e;
        }}
    />
    <CoverBox
        onModChange={(e) => {
            cover_mod = e;
        }}
    />
    <TargetMovement
        onModChange={(e) => {
            movement_mod = e;
        }}
    />
</div>
