<template>
  <header :class="`main-header header-style-one ${sticky ? 'fixed-header' : ''}`">

    <!-- Header Upper -->
    <div class="header-upper">
      <div class="inner-container clearfix">
        <!--Logo-->
        <div class="logo-box">
          <div class="logo"><a href="/" title="Prosearch -  Recruitment Consultants"><img
            src="/images/logo.png" id="thm-logo" alt="Prosearch -  Recruitment Consultants"
            title="Prosearch -  Recruitment Consultants"></a></div>
        </div>
        <div class="nav-outer clearfix">
          <!--Mobile Navigation Toggler-->
          <div class="mobile-nav-toggler">
            <span @click="mobileToggle = !mobileToggle" class="icon flaticon-menu-2"></span><span class="txt">Menu</span>
          </div>

          <!-- Main Menu -->
          <nav class="main-menu navbar-expand-md navbar-light">
            <div class="collapse navbar-collapse show clearfix">
              <ul class="navigation clearfix">
                <li><a href="/">Home</a></li>
                <li class="dropdown"><a href="#">About Us</a>
                  <ul>
                    <li><nuxt-link to="/proprietor-desk">From Proprietors Desk</nuxt-link></li>
                    <li><nuxt-link to="/about-us">About Company</nuxt-link></li>
                  </ul>
                </li>
                <li class="dropdown"><nuxt-link to="#">Services</nuxt-link>
                  <ul>
                    <li><nuxt-link to="/recruitment">Recruitment</nuxt-link></li>
                    <li><nuxt-link to="/training">Training</nuxt-link></li>
                    <li><nuxt-link to="/trading">Trading</nuxt-link></li>
                  </ul>
                </li>
                <li><nuxt-link to="/demand-letter">Demand Letter</nuxt-link></li>
                <li><nuxt-link to="/gallery">Gallery</nuxt-link></li>
                <li><nuxt-link to="/contact">Contact</nuxt-link></li>
                <li><nuxt-link to="/curriculum-vitae">Apply</nuxt-link></li>
              </ul>
            </div>
          </nav>
        </div>

        <div class="other-links clearfix">
          <div class="link-box">
            <div class="call-us">
              <a class="link" href="tel:01817094118">
                <span class="icon"></span>
                <span class="sub-text">Govt. Approved Recruitment Licence No. RL-1027</span>
                <span class="number">Call: 01817094118</span>
              </a>
            </div>
          </div>
        </div>


      </div>
    </div>
    <!--End Header Upper-->

    <nav class="mobile-nav__container">
      <!-- content is loading via js -->

      <div :class="`collapse navbar-collapse ${mobileToggle ? 'show' : ''} clearfix`">
        <ul class="navigation clearfix">
                <li><a href="/">Home</a></li>
                <li class="dropdown"><a href="#">About Us</a>
                  <ul>
                    <li><nuxt-link to="/proprietor-desk">From Proprietors Desk</nuxt-link></li>
                    <li><nuxt-link to="/about-us">About Company</nuxt-link></li>
                  </ul>
                </li>
                <li class="dropdown"><nuxt-link to="#">Services</nuxt-link>
                  <ul>
                    <li><nuxt-link to="/recruitment">Recruitment</nuxt-link></li>
                    <li><nuxt-link to="/training">Training</nuxt-link></li>
                    <li><nuxt-link to="/trading">Trading</nuxt-link></li>
                  </ul>
                </li>
                <li><nuxt-link to="/demand-letter">Demand Letter</nuxt-link></li>
                <li><nuxt-link to="/gallery">Gallery</nuxt-link></li>
                <li><nuxt-link to="/contact">Contact</nuxt-link></li>
                <li><nuxt-link to="/curriculum-vitae">Apply</nuxt-link></li>
              </ul>
      </div>
    </nav>

  </header>
</template>

<script>
  export default {
    name: "Nav",
    data(){
      return {
        sticky: false,
        mobileToggle: false
      }
    },
    mounted() {
      window.addEventListener('scroll', this.handleScroll);

      const mobileNav = document.querySelector('.mobile-nav__container');
      const dropdownMenu = mobileNav.querySelectorAll('.dropdown');
      
      for (let i = 0; i < dropdownMenu.length; i++) {
          dropdownMenu[i].addEventListener("click", function() {
          this.classList.toggle('open');
          this.classList.toggle('current');
          });
      }


    },
    methods: {

      handleScroll() {
        if (window.scrollY > 70) {
          this.sticky = true
        } else if (window.scrollY < 70) {
          this.sticky = false
        }
      },
    }
  }
</script>

<style scoped>

</style>
