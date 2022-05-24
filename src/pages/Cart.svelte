<script>
  import CartComponent from "../components/Cart-Component.svelte";
  import Navbar from '../components/Navbar.svelte';
  import Cart from '../stores/cart-store';
  import { onDestroy } from 'svelte'
  let cart = []
  const links = [
    {
      text: 'Home',
      link: ''
    },
    {
      text: 'Shop',
      link: 'shop'
    },
    {
      text: 'Cart',
      link: 'cart'
    }
  ]

  const unsubscribe = Cart.subscribe(data => cart = data);

  onDestroy(() => {
    unsubscribe()
  })
</script>
<section class="header py-4 px-8 text-gray-50 bg-gray-900 relative">
  <Navbar {links} />
  <div class="my-8">
    <CartComponent {cart} />
  </div>
</section>