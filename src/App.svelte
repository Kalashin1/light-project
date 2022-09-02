<script>
  import Home from "./pages/Home.svelte";
  import Shop from './pages/Shop.svelte';
  import Signup from "./pages/Signup.svelte";
  import Cart from './pages/Cart.svelte';
  import Confirmation from "./pages/Confirmation.svelte";
  import { Router, Route } from "svelte-navigator";
</script>

<Router>
  <Route path="/">
    <Home />
  </Route>
  <Route path="/shop/:lightType/:affiliate" let:params>
    <Shop affiliate="{params.affiliate}" lightType={params.lightType} />
  </Route>
  <Route path="/cart">
    <Cart />
  </Route>
  <Route path="/details">
    <Signup />
  </Route>
  <Route path="/order-placed">
    <Confirmation />
  </Route>
</Router>

