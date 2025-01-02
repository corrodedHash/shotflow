<script>
  import TargetBox from "./lib/TargetBox.svelte";
  import SkyToggle from "./lib/components/SkyToggle.svelte";

  import AdvantageBox from "./lib/regions/AdvantageBox.svelte";
  import RidingBox from "./lib/regions/RidingBox.svelte";
  import ShotConditions from "./lib/regions/ShotConditions.svelte";

  let target_mod = $state(0);
  let mod_change = $derived(target_mod + character_mod);
  let is_shooting = $state(true);
  let character_info = $state();
  let advantage_mod = $state(0);
  let character_mod = $derived(riding_mod + shot_mod + advantage_mod);
  let riding_mod = $state(0);
  let shot_mod = $state(0);
</script>

<main>
  <SkyToggle labelOn="Schuss" labelOff="Wurf" bind:checked={is_shooting} />

  <AdvantageBox
    onCharacterChange={(e) => (character_info = e)}
    onModChange={(e) => (advantage_mod = e)}
  />
  <RidingBox onModChange={(e) => (riding_mod = e)} is_shooting />
  <ShotConditions
    onModChange={(e) => (shot_mod = e)}
    skilllevel={character_info?.skilllevel}
    is_shooting
  />

  <TargetBox
    skilllevel={character_info?.skilllevel}
    onModChange={(e) => {
      target_mod = e;
    }}
  />
  Unter Wasser <br />
  <div>
    Erschwert um {mod_change}
  </div>
</main>
