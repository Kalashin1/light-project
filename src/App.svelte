<script>
  import Home from "./pages/Home.svelte";
  import Shop from './pages/Shop.svelte';
  import Cart from './pages/Cart.svelte';
  import { Router, Route } from "svelte-navigator";
</script>

<Router>
  <Route path="/">
    <Home />
  </Route>
  <Route path="/shop">
    <Shop />
  </Route>
  <Route path="/cart">
    <Cart />
  </Route>
</Router>

