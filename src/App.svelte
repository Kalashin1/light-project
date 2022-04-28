<script>
  import Header from "./components/Header.svelte";
	import HeaderSlideTwo from "./components/Header-SlideTwo.svelte";
  import HeaderSlideThree from "./components/Header-Slide-Three.svelte";
  import { Fullpage, FullpageSection, FullpageSlide } from "svelte-fullpage";
  import Services from "./components/Services.svelte";
  import Pricing from "./components/Pricing.svelte";
  // Optional, include all titles of your sections
  const sectionTitles = ["Home", "History", "Present", "Future"];

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
    <Services />
  </FullpageSection>
  <FullpageSection>
    <Pricing />
  </FullpageSection>
  <FullpageSection>...Your markup here</FullpageSection>
</Fullpage>
