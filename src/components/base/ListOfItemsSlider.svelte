<script>
   import ItemCard from '../base/ItemCard.svelte';

   import { beforeUpdate, onMount } from 'svelte';
   import API from '../../api';
   import HorizontalScrollSlider from '../horizontalScrollSlider/HorizontalScrollSlider.svelte';
   export let requestURL;

   $: list = [];

   beforeUpdate(async () => {});

   onMount(async () => {
      API.get(requestURL).then(res => (list = res.data));
   });
</script>

<HorizontalScrollSlider isItemsExist={list.length > 0}>
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
</HorizontalScrollSlider>
