<template>
  <div>
    <Nav />
    <PageHeader title="About Company" />
    <AgencySection />
    <AboutHeadPage />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Footer from "../components/Footer";
  import AboutHeadPage from "../components/AboutHeadPage";
  import AgencySection from "../components/AgencySection-2";
  export default {
    components: {
      AgencySection,
      AboutHeadPage,
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
