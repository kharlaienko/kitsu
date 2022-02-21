<script>
   import { onMount } from 'svelte';

   import API from '../api';

   $: list = [];

   onMount(() => {
      API.get('anime').then(res => (list = res.data));
   });
</script>
