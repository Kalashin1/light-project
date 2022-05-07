<script>
  import Navbar from '../components/Navbar.svelte'
  import ProductCatalogue from '../components/Product-Catalogue.svelte';
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

<section class="header px-8 text-gray-50 bg-gray-900 relative">
  <Navbar {links} />
  <div class="my-8">
    <ProductCatalogue />
  </div>
</section>