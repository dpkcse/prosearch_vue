<template>
  <div>
    <Nav />
    <PageHeader title="Gallery" />
    <GalleryPage />
    <Footer />
  </div>
</template>
<script>
  import Nav from "../components/Nav";
  import PageHeader from "../components/PageHeader";
  import Footer from "../components/Footer";
  import GalleryPage from "../components/ImgGalleryPage";
  export default {
    components: {
      GalleryPage,
      Footer,
      PageHeader,
      Nav
    },
    head(){
      return {
        title: "Prosearch -  Recruitment Consultants"
      }
    }
  }
</script>
