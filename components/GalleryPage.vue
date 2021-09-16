<template>
  <section class="gallery-section">
    <div class="auto-container">
      <!--MixitUp Galery-->
      <div class="mixitup-gallery">
          <!--Filter-->
          <!-- <div class="filters centered clearfix">
            <ul class="filter-tabs filter-btns clearfix">
              <li class="filter mixitup-control-active" data-role="button" data-filter="all">All<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".romania">ROMANIA<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".ksa">SAUDI ARAB<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".qatar">QATAR<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".bahrain">BAHRAIN<sup></sup></li>
              <li class="filter" data-role="button" data-filter=".uae">UAE<sup></sup></li>
            </ul>
        </div> -->
        <div class="filter-list row">
          <!-- Gallery Item -->
          <div class="gallery-item mix all qatar col-lg-4 col-md-6 col-sm-12" v-for="index in 98" v-bind:key="index">
            <div class="inner-box">
              <figure class="image"><img v-bind:src="`/images/demandletter/${index}.jpg`" alt=""></figure>
              <a v-bind:href="`/images/demandletter/${index}.jpg`" class="lightbox-image overlay-box"
                 data-fancybox="gallery"></a>
              <div class="cap-box">
                <div class="cap-inner">
                  <div class="cat"><span>Demand Letter</span></div>
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
    name: "GalleryPage",
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
