<template>
  <div>
    <Nav />
    <Banner />
    <Services />
    <About />
    <FactSection />
    <TrustedSection />
    <BrandsSection />
    <CallToAction />
    <Footer />
  </div>
</template>

<script>

  import Nav from "../components/Nav";
  import Banner from "../components/Banner";
  import Services from "../components/Services";
  import About from "../components/About";
  import FactSection from "../components/FactSection";
  import TrustedSection from "../components/TrustedSection";
  import BrandsSection from "../components/BrandsSection";
  import CallToAction from "../components/CallToAction";
  import Footer from "../components/Footer";

  export default {
    components: {
      Footer,
      CallToAction,
      BrandsSection,
      TrustedSection,
      FactSection,
      About,
      Services,
      Banner,
      Nav

    }
  }
</script>
