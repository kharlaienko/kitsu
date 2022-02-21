<script>
   import ItemCard from '../components/base/ItemCard.svelte';

   import { beforeUpdate, onMount, tick } from 'svelte';
   import API from '../api';

   export let location;

   $: showLeftBorderShadow = true;
   $: showRightBorderShadow = false;

   $: list = [];

   let slider;

   beforeUpdate(async () => {});

   onMount(async () => {
      API.get('trending/anime?limit=10').then(res => (list = res.data));
      await tick();
      changeBorderShadow();
   });

   function changeBorderShadow() {
      if (slider.scrollLeft > 0) {
         showLeftBorderShadow = true;
      } else {
         showLeftBorderShadow = false;
      }
      if (slider.scrollWidth / 2 < slider.scrollLeft) {
         showRightBorderShadow = false;
      } else {
         showRightBorderShadow = true;
      }
   }
</script>

<div class="relative">
   {#if showLeftBorderShadow && list.length > 0}
      <span class="absolute h-[calc(100%_-_1rem)] w-6 bg-gradient-to-r from-slate-600 left-0 z-10 " />
   {/if}
   <div class="pb-5 gap-4 flex overflow-x-auto " on:scroll={changeBorderShadow} bind:this={slider}>
      {#each list as item}
         <ItemCard
            img={item.attributes.posterImage.medium}
            title={item.attributes.canonicalTitle}
            ageRating={item.attributes.ageRating}
            averageRating={item.attributes.averageRating}
            status={item.attributes.status}
            startDate={item.attributes.startDate}
         />
      {:else}
         no items
      {/each}
   </div>

   {#if showRightBorderShadow && list.length > 0}
      <span class="absolute h-[calc(100%_-_1rem)] w-6 bg-gradient-to-l from-slate-600 right-0 top-0 z-10 " />
   {/if}
</div>
