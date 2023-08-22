<script>
	import { links } from './../helper';
  export let affiliate;
  export let lightType;
  import Navbar from '../components/Navbar.svelte'
  import ProductCatalogue from '../components/Product-Catalogue.svelte';
  import Footer from '../components/Footer.svelte';
  console.log(affiliate);
  localStorage.setItem('affiliate', affiliate);
  
</script>

<section>
  <div class="header px-8 text-gray-50 bg-gray-900 relative">
    <Navbar {links} />
    <div>
      <ProductCatalogue {lightType} />
    </div>
  </div>
  <Footer></Footer>
</section>