<script>
  import Home from "./pages/Home.svelte";
  import Shop from './pages/Shop.svelte';
  import { Router, Route } from "svelte-navigator";
</script>

<Router>
  <Route path="/">
    <Home />
  </Route>
  <Route path="/shop">
    <Shop />
  </Route>
</Router>

