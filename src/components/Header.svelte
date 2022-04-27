<script>
  import Navbar from "./Navbar.svelte";
  import HeaderButton from "./Header-Button.svelte";
  import HeaderText from "./Header-Text.svelte";
</script>

<section class="header md:px-8 text-gray-50 relative">
  <Navbar />
  <div class="md:flex relative justify-center z-20">
    <div class="md:w-1/2">
      <HeaderText text="Lorem ipsum dolor sit amet" />
      <p class="md:my-12 md:px-6">
        Lorem ipsum dolor sit amet consectetur adipiscing elit, vel aliquet dapibus potenti pharetra venenatis. Vulputate sed morbi risus a in ullamcorper arcu, consequat himenaeos rhoncus vel libero eleifend tempor curae, vivamus aliquam penatibus torquent malesuada vitae. consequat himenaeos rhoncus vel libero eleifend tempor curae, vivamus aliquam penatibus torquent malesuada vitae.
      </p>
      <div class="m-4 flex justify-center">
        <HeaderButton text="Buy" />
        <HeaderButton text="More" />
      </div>
    </div>
    <div>
      <!-- <img src="/images/chandelier (2).png" alt="some-dope" class="absolute right-12 -top-8" /> -->
    </div>
  </div>
</section>

<style>
  section.header {
    background: url('/images/luxury-restaurant-grill-bar-interior-with-chandeliers-furniture.jpg');
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
    opacity: .5;
    top: 0; left: 0;
  }
</style>