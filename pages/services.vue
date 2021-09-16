<template>
  <div>
    <Nav />
    <PageHeader title="Services" />
    <ServicesPage />
    <Services />
    <WeWorkSection />
    <CallToActionThree />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Services from "../components/Services";
  import Footer from "../components/Footer";
  import ServicesPage from "../components/ServicesPage";
  export default {
    components: {
      ServicesPage,
      Footer,
      Services,
      PageHeader,
      Nav
    },
    head(){
      return {
        title: "Linoor | Services"
      }
    }
  }
</script>
