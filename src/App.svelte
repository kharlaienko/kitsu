<script>
   import { Router, Route } from 'svelte-navigator';
   import Home from './routes/Home.svelte';
   import About from './routes/About.svelte';
   import Menu from './components/Menu.svelte';
</script>

<main class="bg-slate-500 p-1 text-gray-100 h-screen">
   <Router primary={false}>
      <Menu />
      <div>
         <Route path="/" component={Home} />
         <Route path="about" component={About} />
      </div>
   </Router>
</main>

<style>
   :root {
      font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans',
         'Helvetica Neue', sans-serif;
   }
</style>
