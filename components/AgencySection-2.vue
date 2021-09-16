<template>
  <section class="agency-section">
    <div class="auto-container">
      <div class="row clearfix">
        <!--Left Column-->
        <div class="left-col col-xl-6 col-lg-12 col-md-12 col-sm-12">
          <div class="inner">
            <div class="sec-title">
              <h2>Best RECRUITMENT Agency solutions <span class="dot">.</span></h2>
            </div>

            <!--Default Tabs-->
            <div class="default-tabs tabs-box">

              <div class="agency-tabs">
                <!--Tab-->
                <input type="radio" name="tabs" id="tab-three" checked="checked">
                <label for="tab-three" class="tab-btn">Our History</label>
                <div class="tab">
                  <div class="active-tab">
                    <div class="content">
                      <div class="text">Bangladesh, a country of 140 million people of moderate Muslim and modern democracy, is a potential market for human resources. Our country has close cultural relation with the Middle Eastern and Gulf countries as well as with Malaysia. Our workers are energetic, law abiding, disciplined and peace loving. They inherit a secular culture of a moderate Muslim and democratic tradition. This helps them to work with the workers of any other country and of any religion. They possess a special quality of adjustment in any situation and atmosphere. Presently Bangladesh has over 100 Technical Training centers. Beside 64 Technical Training Institutes in all the 64 District Head Quarters, there are about 50 Technical Training centers in and around the capital. Some run by private ownership, Some by Government in 'joint collaboration’ with ILO. These centers maintain high quality of professional and technical standard.</div>
                      
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <!--Right Column-->
        <div class="right-col col-xl-6 col-lg-12 col-md-12 col-sm-12">
          <div class="inner">
            <div class="text">As such we are capable of supplying all categories of highly skilled, semiskilled as well as unskilled work forces to any country in the world. Our youths are strong and diligent and can adjust to any environment and conditions.</div>
            <div class="text">We are in a position to arrange for recruitment and mobilization of professionally qualified and well-experienced candidates as per your requisition from Bangladesh.</div>
            <div class="featured-block-two clearfix">
              <div class="image"><img src="/images/resource/logo.jpg" alt=""></div>
              <div class="text">
                <ul>
                  <li>Manpower Recruitment.</li>
                  <li>Manpower Training.</li>
                  <li>Enterprise.</li>
                </ul>
              </div>
            </div>
          </div>
        </div>

        <h2>Why choose Prosearch Recruitment Solution<span class="dot">.</span></h2>
        <div class="text">In today's rapidly changing business climate, the efficient and effective organization wins, and that means having people who fit your needs perfectly, when you need them. Whether you need to staff a single facility or support a multi-location national operation with uniquely skilled, semi-skilled or unskilled people, Greenland has recruitment and staffing services to help you meet your goals.</div>
        
        <h2>Advantages over other staffing servies<span class="dot">.</span></h2>
        <div class="text">Specialized divisions & subsidiaries - Specialized recruiters in each of our industry specific divisions & subsidiaries know the unique skills and requirements of each industry and where to locate the best people in that field.</div>
        <div class="text">Carefully screened, qualified candidates - Our comprehensive recruiting, screening and testing process means you get qualified candidates with the skills to fit perfectly into their positions.</div>
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
