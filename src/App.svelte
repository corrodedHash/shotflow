<script>
  import CharacterBox from "./lib/CharacterBox.svelte";
  import TargetBox from "./lib/TargetBox.svelte";
  import SkyToggle from "./lib/components/SkyToggle.svelte";

  let is_shooting = $state(true);
</script>

<main>
  <SkyToggle labelOn="Schuss" labelOff="Wurf" bind:checked={is_shooting} />
  <CharacterBox />
  <TargetBox />
  Unter Wasser <br />
</main>
