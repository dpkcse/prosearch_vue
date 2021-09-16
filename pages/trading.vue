<template>
  <div>
    <Nav />
    <PageHeader title="WE ARE WORK ON IT" />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Footer from "../components/Footer";
  export default {
    components: {
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
