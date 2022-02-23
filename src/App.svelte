<script>
   import { Router, Route } from 'svelte-navigator';
   import Home from './routes/Home.svelte';
   import Detail from './routes/Detail.svelte';
   import Menu from './components/base/Menu.svelte';
</script>

<main class="bg-slate-500 text-gray-100 h-screen overflow-hidden flex flex-col">
   <Router primary={false}>
      <Menu />
      <div class="mt-5 h-full flex flex-col overflow-y-auto">
         <div class="p-2">
            <Route path="/" component={Home} />
            <Route path="/:slug" component={Detail} />
         </div>
      </div>
   </Router>
</main>

<style>
   :root {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans',
         'Helvetica Neue', sans-serif;
   }
</style>
