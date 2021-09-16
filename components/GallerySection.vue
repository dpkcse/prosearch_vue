<template>
  <section class="gallery-section">
    <div class="auto-container">
      <!--MixitUp Galery-->
      <div class="mixitup-gallery">
        <div class="upper-row clearfix">
          <div class="sec-title">
            <h2>Demand Letter <span class="dot">.</span></h2>
          </div>
          <!--Filter-->
          <div class="filters clearfix">
            <ul class="filter-tabs filter-btns clearfix">
              <li class="filter mixitup-control-active" data-role="button" data-filter="all">All<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".romania">ROMANIA<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".ksa">SAUDI ARAB<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".qatar">QATAR<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".bahrain">BAHRAIN<sup></sup></li>
            </ul>
          </div>
        </div>
        <div class="filter-list row">
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania1.jpg" alt=""></figure>
              <a href="/images/demandletter/romania1.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania2.jpg" alt=""></figure>
              <a href="/images/demandletter/romania2.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania3.jpg" alt=""></figure>
              <a href="/images/demandletter/romania3.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania4.jpg" alt=""></figure>
              <a href="/images/demandletter/romania4.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania5.jpg" alt=""></figure>
              <a href="/images/demandletter/romania5.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania6.jpg" alt=""></figure>
              <a href="/images/demandletter/romania6.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania7.jpg" alt=""></figure>
              <a href="/images/demandletter/romania7.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <!-- Gallery Item -->
          <div class="gallery-item mix all romania col-lg-4 col-md-6 col-sm-12">
            <div class="inner-box">
              <figure class="image"><img src="/images/demandletter/romania8.jpg" alt=""></figure>
              <a href="/images/demandletter/romania8.jpg" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Romania</span></div>
                  <div class="title">
                    <h5>Demand Letter</h5>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>

      </div>

    </div>
  </section>
</template>

<script>
  export default {
    name: "GallerySection",
    data () {
      return {
        mixer: null
      }
    },
    mounted () {
        const containerEl = document.querySelector('.filter-list')
        this.mixer = new this.mixitup(containerEl, {
      });

      new GLightbox({
          selector: '.lightbox-image',
          touchNavigation: true,
          loop: true,
          autoplayVideos: true
      });
    },
  }
</script>

<style scoped>

</style>
