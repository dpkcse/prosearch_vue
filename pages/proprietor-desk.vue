<template>
  <div>
    <Nav />
    <PageHeader title="From Proprietors Desk" />
    <ProprietorPage />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Footer from "../components/Footer";
  import ProprietorPage from "../components/ProprietorPage";
  import Testimonial from "../components/Testimonial";
  import FunFacts from "../components/FunFacts";
  import ParallaxSection from "../components/ParallaxSection";
  import AgencySection from "../components/AgencySection";
  import TeamSectionTwo from "../components/TeamSectionTwo";
  import BrandsSectionTwo from "../components/BrandsSectionTwo";
  export default {
    components: {
      BrandsSectionTwo,
      TeamSectionTwo,
      AgencySection,
      ParallaxSection,
      FunFacts,
      Testimonial,
      ProprietorPage,
      Footer,
      PageHeader,
      Nav
    },
    head(){
      return {
        title: "Prosearch -  Recruitment Consultants | Curriculum Vitae"
      }
    }
  }
</script>
