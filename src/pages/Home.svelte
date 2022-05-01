<script>
  import Header from "../components/Header.svelte";
	import HeaderSlideTwo from "../components/Header-SlideTwo.svelte";
  import HeaderSlideThree from "../components/Header-Slide-Three.svelte";
  import { Fullpage, FullpageSection, FullpageSlide } from "svelte-fullpage";
  import Services from "../components/Services.svelte";
  import Pricing from "../components/Pricing.svelte";
  import About from "../components/About.svelte";
  import ContactUs from '../components/Contact-Us.svelte'
  import Footer from '../components/Footer.svelte'
  // Optional, include all titles of your sections
  const sectionTitles = ["Home", "About", "Services", "Plans", "Contact", "Footer"];

  // Same mechanics as in sections
  const slideTitles = ["1982-1993", "1993-2006", "2006-present"];

</script>

<Fullpage {sectionTitles} arrows>
  <FullpageSection center {slideTitles} arrows>
    <FullpageSlide>
			<Header />
		</FullpageSlide>
    <FullpageSlide>
			<HeaderSlideTwo />
		</FullpageSlide>
    <FullpageSlide>
      <HeaderSlideThree />
    </FullpageSlide>
  </FullpageSection>
  <FullpageSection>
    <About />
  </FullpageSection>
  <FullpageSection>
    <Services />
  </FullpageSection>
  <FullpageSection>
    <Pricing />
  </FullpageSection>
  <FullpageSection>
    <ContactUs />
  </FullpageSection>
  <FullpageSection>
    <Footer />
  </FullpageSection>
</Fullpage>
