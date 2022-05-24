<script>
	import HeaderSlideTwo from "../components/Header-SlideTwo.svelte";
  import Services from "../components/Services.svelte";
  import About from "../components/About.svelte";
  import ContactUs from '../components/Contact-Us.svelte'
  import Footer from '../components/Footer.svelte'
  // Optional, include all titles of your sections
  const sectionTitles = ["Home", "About", "Services", "Contact", "Footer"];

  // Same mechanics as in sections
  const slideTitles = ["1982-1993", "1993-2006", "2006-present"];
  
</script>


<HeaderSlideTwo />
<About />
<Services />
<ContactUs />
<Footer />

<!-- <Fullpage {sectionTitles} arrows>
  <FullpageSection>
    <HeaderSlideTwo />
  </FullpageSection>
  <FullpageSection>
    <About />
  </FullpageSection>
  <FullpageSection>
    <Services />
  </FullpageSection>
  <FullpageSection>
    <ContactUs />
  </FullpageSection>
  <FullpageSection>
    <Footer />
  </FullpageSection>
</Fullpage> -->
