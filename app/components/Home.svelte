<script lang="ts">
  import { navigate } from "svelte-native";
  import Details from "./Details.svelte";

  function onButtonTap() {
    navigate({
      page: Details,
    });
  }
</script>

<page>
  <actionBar title="Home" />
  <stackLayout>
    <button text="Tap me" on:tap={onButtonTap} />
  </stackLayout>
</page>

<style>
</style>
