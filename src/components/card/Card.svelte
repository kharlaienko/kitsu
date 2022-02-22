<script>
   import RatingBage from '../base/RatingBage.svelte';
   import Link from '../base/Link.svelte';
   export let img;
   export let title;
   export let ageRating;
   export let averageRating;
   export let status;
   export let startDate;
   export let slug;

   $: startYear = startDate.slice(0, 4);
</script>

<div class=" bg-red-800 w-full h-auto relative rounded-lg shadow-md shadow-slate-700 sm:w-48 shrink-0">
   <div class="max-w-full h-full rounded-lg">
      <img class="w-full h-full object-cover rounded-lg" src={img} alt={title} />
   </div>

   <div
      class="rounded-lg absolute opacity-0 top-0 left-0 h-full w-full overflow-hidden hover:opacity-100 bg-slate-700 bg-opacity-70 transition"
   >
      <div class="flex flex-col h-full p-2">
         <div class="flex items-center justify-between">
            <div class="capitalize">{status}</div>
            <RatingBage rating={averageRating} />
         </div>
         <div class="flex items-center justify-between">
            <div>Age: {ageRating}</div>
            <div class="ml-auto mt-2">{startYear}</div>
         </div>

         <h3 class="text-lg leading-5 my-auto text-center">{title}</h3>

         <Link link={slug}>Details</Link>
      </div>
   </div>
</div>
