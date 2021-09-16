<template>
  <section class="services-section">
    <div class="auto-container">
      <div class="row clearfix">
        <!--Title Block-->
        <div class="title-block col-xl-12 col-lg-12 col-md-12 col-sm-12">
          <div class="inner">
            <div class="sec-title">
              <h2>We Shape the Perfect Solutions<span class="dot">.</span></h2>
              <div class="lower-text">We are committed to providing our customers with exceptional
                service while offering our employees the best training.</div>
            </div>
          </div>
        </div>
        <!--Service Block-->
        <div class="service-block col-xl-3 col-lg-6 col-md-6 col-sm-12 wow fadeInLeft" data-wow-delay="0ms"
             data-wow-duration="1500ms">
          <div class="inner-box recruitment">
            <div class="bottom-curve"></div>
            <h6><nuxt-link to="#">Recruitment <br>Consultant</nuxt-link></h6>
          </div>
        </div>
        <!--Service Block-->
        <div class="service-block col-xl-3 col-lg-6 col-md-6 col-sm-12 wow fadeInLeft"
             data-wow-delay="300ms" data-wow-duration="1500ms">
          <div class="inner-box traningfacility">
            <div class="bottom-curve"></div>
            <h6><nuxt-link to="#">Training <br>Facility</nuxt-link></h6>
          </div>
        </div>
        <!--Service Block-->
        <div class="service-block col-xl-3 col-lg-6 col-md-6 col-sm-12 wow fadeInLeft" data-wow-delay="0ms"
             data-wow-duration="1500ms">
          <div class="inner-box japaneselangu">
            <div class="bottom-curve"></div>
            <h6><nuxt-link to="#">Japanese Language <br>Center</nuxt-link></h6>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
    export default {
        name: "Services"
    }
</script>

<style scoped>

</style>
