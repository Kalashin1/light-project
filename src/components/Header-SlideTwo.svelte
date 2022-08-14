<script>
  import Navbar from "./Navbar.svelte";
  import HeaderButton from "./Header-Button.svelte";
  import HeaderText from "./Header-Text.svelte";
  import HeaderParagraph from "./Header-paragraph.svelte";

  let links = [
    {
      text: 'Home',
      link: ''
    },
    {
      text: 'Shop',
      link: 'shop'
    }
  ]
</script>

<section class="header text-gray-50 relative">
  <Navbar { links } />
  <div class="md:flex mt-16 relative justify-center z-20 py-4 px-8">
    <div class="md:w-1/2">
      <HeaderText text="Helvic Gleam" />
      <HeaderParagraph />
      <div class="m-4 flex justify-center">
        <HeaderButton route="shop" text="Check Out Our Store" />
      </div>
    </div>
    <div>
      <!-- <img src="/images/chandelier (2).png" alt="some-dope" class="absolute right-12 -top-8" /> -->
    </div>
  </div>
</section>

<style>
  section.header {
    background: url('/images/beautiful-luxury-chandelier-decoration-interior-min.jpg');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    min-height: 100vh;
  }

  section.header::before{
    content: '';
    background-color: black;
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: 2;
    opacity: .4;
    top: 0; left: 0;
  }
</style>