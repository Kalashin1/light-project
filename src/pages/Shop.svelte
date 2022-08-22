<script>
  export let affiliate;
  import Navbar from '../components/Navbar.svelte'
  import ProductCatalogue from '../components/Product-Catalogue.svelte';
  import Footer from '../components/Footer.svelte';
  console.log(affiliate);
  localStorage.setItem('affiliate', affiliate);
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

<section>
  <div class="header px-8 text-gray-50 bg-gray-900 relative">
    <Navbar {links} />
    <div>
      <ProductCatalogue />
    </div>
  </div>
  <Footer></Footer>
</section>