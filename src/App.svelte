<script lang="ts">
  import { tweened } from "svelte/motion";
  import Counter from "./lib/Counter.svelte";
  import HeroSection from "./lib/heroSection.svelte";
  import Nav from "./lib/nav.svelte";
  import { onMount } from "svelte";
  let scale = tweened(1);
  onMount(() => {
    scale.set(2);
  });
</script>

<Nav />
<main class="flex justify-around items-center h-full">
  <HeroSection />
  <div
    style={`--scale: ${$scale}`}
    class="btn w-20 h-20 rounded-full bg-white grid place-items-center text-black text-sm tracking-widest"
  >
    <span>EXPLORE</span>
  </div>
</main>

<style>
  .btn {
    font-family: "Barlow Condensed", sans-serif;
    transform: scale(var(--scale));
  }
</style>
