<script lang="ts">
  import { onMount } from "svelte";

  export let activeIndex = 0;
  let indicator: HTMLElement;

  let navArray: {
    name: string;
    ref: null | HTMLElement;
    link: string;
    id: string;
  }[] = [
    {
      name: "home",
      link: "/",
      id: "01",
      ref: null,
    },
    {
      name: "destination",
      link: "/destination",
      id: "02",
      ref: null,
    },
    {
      name: "crew",
      link: "/crew",
      id: "03",
      ref: null,
    },
    {
      name: "technology",
      link: "/technology",
      id: "04",
      ref: null,
    },
  ];
  let menuItemWidth = 100;
  let indicatorPos = 0;
  let loaded = false;
  onMount(() => {
    loaded = true;
  });
  $: {
    if (loaded) {
      let activeMenu = navArray[activeIndex].ref as HTMLElement;
      let dim = activeMenu.getBoundingClientRect();
      let width = dim.width as number;
      let left =
        dim?.left - activeMenu.parentElement.getBoundingClientRect().left;
      menuItemWidth = width;
      indicator.style.width = menuItemWidth + "px";
      indicatorPos = left;
    }
  }
</script>

<nav class="flex pt-8 pl-5 items-center">
  <div class="brand w-10 h-10 shrink-0">
    <img src="./assets/shared/logo.svg" alt="logo" class="w-10 h-10" />
  </div>
  <span class="line w-full h-[0.1px] translate-x-10 z-10" />
  <div
    class=" ml-auto menu flex transition-all gap-10 items-center lg:w-[100%] py-4 pl-20 pr-[10%] relative"
    role="menu"
  >
    <div
      bind:this={indicator}
      style="--indicatorPos: {indicatorPos}px"
      class="z-20 activeIndicator transition-all duration-300 absolute h-0.5 translate-x-1 bg-white bottom-0"
    />
    {#each navArray as navItem (navItem.id)}
      <button
        bind:this={navItem.ref}
        class="nav-item flex items-center gap-2"
        role="menuitem"
        tabindex="0"
        on:click={() => {
          activeIndex = navArray.indexOf(navItem);
        }}
      >
        <span class="text-sm font-bold">{navItem.id}</span>
        <span class="text-sm font-light uppercase">{navItem.name}</span>
      </button>
    {/each}
  </div>
</nav>

<style>
  .menu {
    background-color: rgba(37, 69, 103, 0.2);
    backdrop-filter: blur(20px);
  }
  .line {
    background-color: hsl(231, 10%, 25%);
  }
  .activeIndicator {
    left: var(--indicatorPos);
  }
</style>
