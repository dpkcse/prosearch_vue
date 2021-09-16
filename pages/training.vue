<template>
  <div>
    <Nav />
    <PageHeader title="TRAINING" />
    <Tranning />
    <Course />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Footer from "../components/Footer";
  import Course from "../components/Course";
  import Tranning from "../components/Tranning";
  export default {
    components: {
      Tranning,
      Course,
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
