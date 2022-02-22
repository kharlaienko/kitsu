<script>
   import { Link } from 'svelte-navigator';

   export let link;
</script>

<Link
   to={link}
   class="mt-auto flex items-center bg-slate-600 rounded border-solid p-3 mx-auto delay-100 group hover:text-gray-50"
>
   <slot />
   <p />

   <svg xmlns="http://www.w3.org/2000/svg" class="ml-2 h-4 w-4 " fill="none" viewBox="0 0 24 24" stroke="currentColor">
      <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 5l7 7-7 7M5 5l7 7-7 7" />
   </svg>
</Link>
