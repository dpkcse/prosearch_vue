<template>
  <div>
  <footer class="main-footer">
    <div class="auto-container">
      <!--Widgets Section-->
      <div class="widgets-section">
        <div class="row clearfix">

          <!--Column-->
          <div class="column col-xl-3 col-lg-6 col-md-6 col-sm-12">
            <div class="footer-widget logo-widget">
              <div class="widget-content">
                <div class="logo">
                  <nuxt-link to="/"><img id="fLogo" src="/images/footer-logo.png" alt="" /></nuxt-link>
                </div>
                <div class="text">You will be glad for choosing the Prosearch Recruitment Consultant as your people partner. We assure that you will be safe profitable with the quality service and better co-operation in future.</div>
                <ul class="social-links clearfix">
                  <li><a href="https://www.facebook.com/prosearchrecruitment"><span class="fab fa-facebook-square"></span></a></li>
                  <li><a href="#"><span class="fab fa-twitter"></span></a></li>
                  <li><a href="#"><span class="fab fa-instagram"></span></a></li>
                  <li><a href="#"><span class="fab fa-pinterest-p"></span></a></li>
                </ul>
              </div>
            </div>
          </div>

          <!--Column-->
          <div class="column col-xl-3 col-lg-6 col-md-6 col-sm-12">
            <div class="footer-widget links-widget">
              <div class="widget-content">
                <h6>Explore</h6>
                <div class="row clearfix">
                  <div class="col-md-6 col-sm-12">
                    <ul>
                      <li><a href="/about-us">About</a></li>
                      <li><a href="/recruitment">Recruitment</a></li>
                      <li><a href="/demand-letter">Demand Letter</a></li>
                      <li><a href="/gallery">Gallery</a></li>
                      <li><a href="/contact">Contact</a></li>
                    </ul>
                  </div>
                </div>
              </div>
            </div>
          </div>

          <!--Column-->
          <div class="column col-xl-3 col-lg-6 col-md-6 col-sm-12">
            <div class="footer-widget info-widget">
              <div class="widget-content">
                <h6>Contact</h6>
                <ul class="contact-info">
                  <li class="address"><span class="icon flaticon-pin-1"></span> City Heart (13th floor), Suite-07, 67 Naya paltan, Dhaka-1000</li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 02 9344102">TEL : +88 02 8332935</a></li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 02 9344102">TEL : +88 02 22222402</a></li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 01817094118">Mobile: +88 01817094118</a></li>
                  <li><span class="icon flaticon-email-2"></span><a href="mailto:modern_brs@yahoo.com">rdroni_dhaka@yahoo.com</a></li>
                  <li><span class="icon flaticon-email-2"></span><a href="mailto:rdronidhaka@gmail.com">rdronidhaka@gmail.com</a></li>
                </ul>
              </div>
            </div>
          </div>

          <!--Column-->
          <div class="column col-xl-3 col-lg-6 col-md-6 col-sm-12">
            <div class="footer-widget newsletter-widget">
              <div class="widget-content">
                <h6>Company Profile</h6>
                <div class="text"><a href="/profile/prosearch-recruitment-consultants.pdf" target="_BLANK"><span class="icon flaticon-down"> </span> Click here to download profile</a></div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer Bottom -->
    <div class="footer-bottom">
      <div class="auto-container">
        <div class="inner clearfix">
          <div class="copyright">&copy; copyright 2021 by prosearchrecruit.com Develop by Devs Flock</div>
        </div>
      </div>
    </div>

  </footer>

    <a @click="scrollTop" class="scroll-to-target scroll-to-top" :style="`display: ${scrollBtn ? 'inline' : 'none'}`" href="#"><i class="fa fa-angle-up"></i></a>

  </div>

</template>

<script>
  export default {
    name: "Footer",
    data(){
      return {
        scrollBtn: false
      }
    },
    mounted() {
      window.addEventListener('scroll', this.handleScroll);
    },

    methods: {

      handleScroll () {

        if (window.scrollY > 70) {
          this.scrollBtn = true
        }
        else if (window.scrollY < 70) {
          this.scrollBtn = false
        }
      },

      scrollTop () {
        window.scrollTo(0, 0);
      }


    }
  }
</script>

<style scoped>

</style>
