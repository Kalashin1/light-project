<script>
  import { onMount } from 'svelte'
  import Loader from '../components/Loader.svelte';
	import HeaderSlideTwo from "../components/Header-SlideTwo.svelte";
  import Services from "../components/Services.svelte";
  import About from "../components/About.svelte";
  import ContactUs from '../components/Contact-Us.svelte'
  import Footer from '../components/Footer.svelte'
  // Optional, include all titles of your sections
  const sectionTitles = ["Home", "About", "Services", "Contact", "Footer"];

  // Same mechanics as in sections
  const slideTitles = ["1982-1993", "1993-2006", "2006-present"];
  const wakeServer = async () => {
    setTimeout(() => {
      showLoader = false;
    }, 500);
  }

  onMount(async () => {
    await wakeServer();
  })

  $:showLoader = true;

</script>


{#if showLoader}
  <div class="bg-gray-800 flex items-center justify-center h-screen">
    <Loader />
    <h3 class="text-white">Loading...</h3>
  </div>
{:else}
  <HeaderSlideTwo />
    <About />
    <Services />
    <ContactUs />
  <Footer />
{/if}





