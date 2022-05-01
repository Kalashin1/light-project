<script>
  import Navbar from '../components/Navbar.svelte'
  import ProductCatalogue from '../components/Product-Catalogue.svelte';
  import CartComponent from '../components/Cart-Component.svelte';
  const links = [
    'home',
    'shop',
    'cart'
  ]
</script>

<section class="header px-8 text-gray-50 bg-gray-900 relative">
  <Navbar {links} />
  <div class="my-8">
    <ProductCatalogue />
    <CartComponent />
  </div>
</section>