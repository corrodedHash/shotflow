<script>
  import CharacterBox from "./lib/CharacterBox.svelte";
  import TargetBox from "./lib/TargetBox.svelte";
  import SkyToggle from "./lib/components/SkyToggle.svelte";

  let target_mod = $state(0);
  let character_mod = $state(0);
  let mod_change = $derived(target_mod + character_mod);
  let is_shooting = $state(true);
</script>

<main>
  <SkyToggle labelOn="Schuss" labelOff="Wurf" bind:checked={is_shooting} />
  <CharacterBox is_shooting bind:mod_change={character_mod} />
  <TargetBox bind:mod_change={target_mod} />
  Unter Wasser <br />
  <div>
    Erschwert um {mod_change}
  </div>
</main>
