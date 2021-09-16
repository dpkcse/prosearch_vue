<template>
  <div>
    <Nav />
    <PageHeader title="Curriculum Vitae" />
    <CurriculumPage />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Footer from "../components/Footer";
  import CurriculumPage from "../components/CurriculumPage";
  export default {
    components: {
      CurriculumPage,
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
