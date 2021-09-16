<template>

  <div>

    <section class="banner-section banner-one">
      <div class="left-based-text">
        <div class="base-inner">
          <div class="hours">
            <ul class="clearfix">
              <li><span>sat - thu</span></li>
              <li><span>9am - 7pm</span></li>
            </ul>
          </div>
          <div class="social-links">
            <ul class="clearfix">
              <li><a href="#"><span>Twitter</span></a></li>
              <li><a href="https://www.facebook.com/prosearchrecruitment" target="_BLANK"><span>Facebook</span></a></li>
            </ul>
          </div>
        </div>
      </div>

      <div class="banner-carousel">

        <no-ssr> <!-- important to add no-ssr-->
          <carousel :items="1">
        <!-- Slide Item -->
        <div class="slide-item">
          <div class="image-layer" style="background-image: url(/images/main-slider/prosearchBanner1.jpg);"></div>
          <div class="left-top-line"></div>
          <div class="right-bottom-curve"></div>
          <div class="right-top-curve"></div>
          <div class="auto-container">
            <div class="content-box">
              <div class="content">
                <div class="inner">
                  <div class="sub-title">welcome to</div>
                  <h2 style="color:#ffffff;">PROSEARCH  <br>RECRUITMENT CONSULTANTS</h2>
                  <div class="link-box">
                    <nuxt-link class="theme-btn btn-style-one" to="/curriculum-vitae">
                      <i class="btn-curve"></i>
                      <span class="btn-title">Send Your CV</span>
                    </nuxt-link>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

        <!-- Slide Item -->
        <div class="slide-item">
          <div class="image-layer" style="background-image: url(/images/main-slider/prosearchBanner2.jpg);"></div>
          <div class="left-top-line"></div>
          <div class="right-bottom-curve"></div>
          <div class="right-top-curve"></div>
          <div class="auto-container">
            <div class="content-box">
              <div class="content">
                <div class="inner">
                  <div class="sub-title">welcome to</div>
                  <h2 style="color:#ffffff;">PROSEARCH  <br>RECRUITMENT CONSULTANTS</h2>
                  <div class="link-box">
                    <nuxt-link class="theme-btn btn-style-one" to="/curriculum-vitae">
                      <i class="btn-curve"></i>
                      <span class="btn-title">Send Your CV</span>
                    </nuxt-link>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

          </carousel>
        </no-ssr>

      </div>
    </section>

  </div>

</template>

<script>

  export default {
    name: "Banner",
  }
</script>

<style scoped>

</style>
