<script>
	import { links } from './../helper.js';
  import CartComponent from "../components/Cart-Component.svelte";
  import Navbar from '../components/Navbar.svelte';
  import Cart from '../stores/cart-store';
  import { onDestroy } from 'svelte'
  let cart = [];

  const unsubscribe = Cart.subscribe(data => cart = data);

  onDestroy(() => {
    unsubscribe()
  })

  function handleEditAmount(event) {
		console.log(event.detail);
    const item = cart.find(i => i.id == event.detail.id);
    const filteredItem = cart.filter(v => v.id !== item.id)
    console.log(item, filteredItem)
    item.amount += event.detail.amount
    cart = [item, ...filteredItem];
	}
</script>
<section class="header py-4 px-8 text-gray-50 bg-gray-900 relative">
  <Navbar {links} />
  <div class="my-8">
    <CartComponent {cart} on:editAmount={handleEditAmount} />
  </div>
</section>