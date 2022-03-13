<script>
   export let name;
   export let value = '';
</script>

<div class="flex gap-x-5">
   <p class="w-1/3">{name}</p>
   <div>
      <p>{value}</p>
      <slot />
   </div>
</div>
