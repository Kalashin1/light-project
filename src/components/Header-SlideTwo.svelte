<script>
  import Navbar from "./Navbar.svelte";
  import HeaderButton from "./Header-Button.svelte";
  import HeaderText from "./Header-Text.svelte";
  import HeaderParagraph from "./Header-paragraph.svelte";
</script>

<section class="header px-8 text-gray-50 relative">
  <Navbar />
  <div class="md:flex relative justify-center z-20">
    <div class="md:w-1/2">
      <HeaderText text="Lorem ipsum dolor sit amet" />
      <HeaderParagraph />
      <div class="m-4 flex justify-center1">
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
    background: url('/images/beautiful-luxury-chandelier-decoration-interior.jpg');
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