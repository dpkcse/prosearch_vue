<template>
  <section class="agency-section">
    <div class="auto-container">
      <div class="row clearfix">
        <!--Left Column-->
        <div class="left-col col-xl-6 col-lg-12 col-md-12 col-sm-12">
          <div class="inner">
            <div class="sec-title">
              <h2>Space <span class="dot">.</span></h2>
            </div>

            <div class="text">We owe a training center of 30000Sq Ft land named "Modern Training Center" is situated at Barua, Lanjani Para, Khilkhet (Near Airport), Dhaka for skill development of outgoing workers in various trades.</div>
          </div>
        </div>
        <!--Right Column-->
        <div class="right-col col-xl-6 col-lg-12 col-md-12 col-sm-12">
          <div class="inner">
            <div class="sec-title">
              <h2>Standards <span class="dot">.</span></h2>
            </div>
            <div class="text">Our understanding of best practice, international standards, and industry regulations, ensures real workplace challenges.</div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
    export default {
      name: "AgencySection"
    }
</script>

<style>

  .agency-tabs {
    display: flex;
    flex-wrap: wrap;
  }
  .agency-tabs label {
    order: 1;
    display: block;
    padding: 4px 31px;
    margin-right: 0.2rem;
    cursor: pointer;
    background: #FFAA17;
    font-weight: 500;
    transition: background ease 0.2s;
    font-size: 18px;
    text-transform: uppercase;
    color: #222;
  }
  .agency-tabs .tab {
    order: 99;
    flex-grow: 1;
    width: 100%;
    display: none;
    padding: 1rem;
    background: #F4F5F8;
  }
  .default-tabs .agency-tabs .text {
    position: relative;
    font-size: 20px;
    font-weight: 300;
    color: var(--thm-text);
    line-height: 1.7em;
    letter-spacing: 2px;
  }
  .agency-tabs input[type="radio"] {
    display: none;
  }
  .agency-tabs input[type="radio"]:checked + label {
    background: #F4F5F8;
  }
  .agency-tabs input[type="radio"]:checked + label + .tab {
    display: block;
  }

  @media (max-width: 45em) {
    .agency-tabs .tab,
    .agency-tabs label {
      order: initial;
    }
    .agency-tabs label {
      width: 100%;
      margin-right: 0;
      margin-top: 0.2rem;
    }
  }

</style>
