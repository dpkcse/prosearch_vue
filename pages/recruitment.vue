<template>
  <div>
    <Nav />
    <PageHeader title="Recruitment" />
    <Recruitment />
    <Category />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Footer from "../components/Footer";
  import Recruitment from "../components/Recruitment";
  import Category from "../components/Category";
  export default {
    components: {
      Recruitment,
      Category,
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
