<script lang="ts">
  import { onMount } from "svelte";
  import { cubicOut, linear } from "svelte/easing";
  import { fade, fly } from "svelte/transition";
  let isLoaded = false;
  onMount(() => {
    isLoaded = true;
  });
</script>

{#if isLoaded}
  <div class="hero flex flex-col gap-4" in:fly={{ x: -200, duration: 1500 }}>
    <p class="mini-txt text-md">SO, YOU WANT TO TRAVEL TO</p>
    <h1 class="head text-8xl">SPACE</h1>
    <p class="detail text-sm">
      Let’s face it; if you want to go to space, you might as well genuinely go
      to outer space and not hover kind of on the edge of it. Well sit back, and
      relax because we’ll give you a truly out of this world experience!
    </p>
  </div>
{/if}

<style>
  .hero {
    width: min-content;
  }
  .mini-txt {
    font-family: oswald;
    text-transform: uppercase;
    letter-spacing: 2px;
    font-weight: 400;
    color: rgba(255, 255, 255, 0.5);
    font-size: 15px;
    line-height: 25px;
  }
  .detail {
    font-family: "Barlow Condensed";
    font-weight: 400;
    font-size: 14px;
    line-height: 20px;
    color: rgba(255, 255, 255, 0.75);
    letter-spacing: 2px;
  }
  .head {
    font-family: "Bellefair";
    letter-spacing: 20px;
    text-transform: uppercase;
    font-weight: 400;
  }
</style>
