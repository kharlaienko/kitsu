<script>
   import { onMount, tick } from 'svelte';

   $: showLeftBorderShadow = true;
   $: showRightBorderShadow = false;
   export let isItemsExist;
   export let title = '';

   let slider;

   onMount(async () => {
      await tick();
      changeBorderShadow();
   });

   function changeBorderShadow() {
      const isStartScrolling = slider.scrollLeft > 0;
      const isScrolledTillEnd =
         slider.scrollWidth - slider.offsetWidth != 0 && slider.scrollWidth - slider.offsetWidth === slider.scrollLeft;

      showLeftBorderShadow = isStartScrolling;
      showRightBorderShadow = !isScrolledTillEnd;
   }
</script>

{#if title}
   <h3 class="text-xl uppercase mb-2 text-shadow">
      {title}
   </h3>
{/if}

<div class="relative">
   {#if showLeftBorderShadow && isItemsExist}
      <span class="absolute h-[calc(100%_-_1rem)] w-6 bg-gradient-to-r from-slate-600 left-0 z-10 " />
   {/if}
   <div class="pb-5 gap-4 flex overflow-x-auto " on:scroll={changeBorderShadow} bind:this={slider}>
      <slot />
   </div>

   {#if showRightBorderShadow && isItemsExist}
      <span class="absolute h-[calc(100%_-_1rem)] w-6 bg-gradient-to-l from-slate-600 right-0 top-0 z-10 " />
   {/if}
</div>
