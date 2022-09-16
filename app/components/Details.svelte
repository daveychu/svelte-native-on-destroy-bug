<script lang="ts">
  import { onDestroy, onMount } from "svelte";
  import { navigate } from "svelte-native";
  import Home from "./Home.svelte";

  let interval1: ReturnType<typeof setInterval>;

  onMount(async function () {
    console.log("Starting interval 1");
    interval1 = setInterval(() => console.log("1"), 1000);
    console.log("Starting interval 2");
    const interval2 = setInterval(() => console.log("2"), 1000);

    return () => {
      console.log("Destroyed via onMount returned function");
      clearInterval(interval2);
    };
  });

  onDestroy(async function () {
    console.log("Destroyed via onDestroy");
    clearInterval(interval1);
  });

  function onButtonTap() {
    navigate({
      page: Home,
    });
  }
</script>

<page>
  <actionBar title="Details" />
  <stackLayout>
    <button text="Tap me" on:tap={onButtonTap} />
  </stackLayout>
</page>

<style>
</style>
