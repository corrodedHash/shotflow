<script>
  import TargetBox from "./lib/TargetBox.svelte";
  import SkyToggle from "./lib/components/SkyToggle.svelte";
  import RidingBox from "./lib/regions/RidingBox.svelte";
  import ShotConditions from "./lib/regions/ShotConditions.svelte";
  import SkillLevel from "./lib/SkillLevel.svelte";
  import DistanceSense from "./lib/regions/DistanceSense.svelte";
  import DistanceInput from "./lib/DistanceInput.svelte";
  import HandicapBox from "./lib/regions/HandicapBox.svelte";
  import DarkVision from "./lib/regions/DarkVision.svelte";
  import SkyCheck from "./lib/components/SkyCheck.svelte";
  import ViewSituation from "./lib/regions/ViewSituation.svelte";

  let target_mod = $state(0);
  let mod_change = $derived(target_mod + character_mod);
  let is_shooting = $state(true);
  let nightblind = $state(false);
  let darkvision = $state();
  let skilllevel = $state();
  let advantage_mod = $state(0);
  let character_mod = $derived(riding_mod + shot_mod + advantage_mod);
  let riding_mod = $state(0);
  let shot_mod = $state(0);
  let view_mod = $state(0);
  let handicap_mod = $state(0);
  let distance = $state(0);
</script>

<main>
  <SkyToggle labelOn="Schuss" labelOff="Wurf" bind:checked={is_shooting} />
  <DistanceInput bind:distance />
  <SkillLevel onSkilllevelChange={(e) => (skilllevel = e)} />
  <SkyCheck bind:checked={nightblind} label="Nachtblind" />
  <DarkVision onDarkvisionChange={(e) => (darkvision = e)} />
  <HandicapBox onModChange={(e) => (handicap_mod = e)} {distance} />
  <DistanceSense onModChange={(e) => (advantage_mod = e)} />
  <RidingBox onModChange={(e) => (riding_mod = e)} {is_shooting} />

  <ViewSituation
    onModChange={(e) => {
      view_mod = e;
    }}
    {darkvision}
    {nightblind}
  />
  <ShotConditions
    onModChange={(e) => (shot_mod = e)}
    {skilllevel}
    {is_shooting}
  />

  <TargetBox
    {skilllevel}
    onModChange={(e) => {
      target_mod = e;
    }}
  />
  Unter Wasser <br />
  <div>
    Erschwert um {mod_change}
  </div>
</main>
