<script>
   import RatingBage from '../components/base/RatingBage.svelte';
   import InfoItem from '../components/Details/InfoItem.svelte';
   import { onMount } from 'svelte';

   import API from '../api';
   export let slug;

   $: item = {};

   onMount(async () => {
      const { data } = await API.get(`anime?filter[slug]=${slug}`);
      item = data[0];
   });
</script>

<div class="sm:flex gap-x-5">
   <div class="mb-5 sm:w-1/3 sm:mb-0">
      <div class="w-full relative rounded">
         <img class="w-full rounded" src={item?.attributes?.posterImage?.large} />
      </div>
   </div>

   <div class="text-2xl flex-grow">
      <InfoItem name={'Title:'} value={item?.attributes?.canonicalTitle} />

      <InfoItem name={'Rating:'}>
         <RatingBage rating={item?.attributes?.averageRating} />
      </InfoItem>

      <InfoItem name={'Age Rating:'} value={item?.attributes?.ageRating} />
   </div>
</div>
