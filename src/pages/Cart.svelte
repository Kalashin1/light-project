<script>
  import CartComponent from "../components/Cart-Component.svelte";
  import Navbar from '../components/Navbar.svelte'
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
</script>
<section class="header py-4 px-8 text-gray-50 bg-gray-900 relative">
  <Navbar {links} />
  <div class="my-8">
    <CartComponent />
  </div>
</section>