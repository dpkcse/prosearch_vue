<template>
  <section class="agency-section">
    <div class="auto-container">
      <div class="row clearfix">
        <!--Left Column-->
        <div class="left-col col-xl-6 col-lg-12 col-md-12 col-sm-12">
          <div class="inner">
            <div class="sec-title">
              <h2>Required Documents From Employers <span class="dot">.</span></h2>
            </div>

            <div class="text">1. Demand Letter, Power of Attorney and Specimen Work Agreement documents duly attested by Bangladeshi Embassy.</div>
            <div class="text">2. All visa documents for the candidates</div>
            <div class="text">3. Joining Tickets</div>
            <div class="text"><strong>Issuance of demand letter:</strong> A formal letter issued by the employer addressing “Prosearch Recruitment Consultant” Stating the type of category, number of worker, salary, period of contact working hours and all possible facilities like food, lodging, medical, Air passage etc.</div>
            <div class="text"><strong>Power of Attorney:</strong> A letter issued by the employer authorizing “Prosearch Recruitment Consultant” to act onbehalf of the employer in recruiting demander worker and to carry out all necessary formalities related with the respective embassy and the related agencies of the Government of Bangladesh.</div>
            <div class="text"><strong>Visa Advice/NOC/Work Permit:</strong> Documents Granting Permission From the appropriate Authority of the company of employment for recruitment of Bangladesh workers in the Form of visa advice / NOC/Work permit is sent to the “Prosearch Recruitment Consultant”.</div>
            <div class="text"><strong>Employment Contract:</strong> Employment contract duly signed between the employer and the employee.</div>
          </div>
        </div>
        <!--Right Column-->
        <div class="right-col col-xl-6 col-lg-12 col-md-12 col-sm-12">
          <div class="inner">
            <div class="sec-title">
              <h2>Human Resources <span class="dot">.</span></h2>
            </div>
            <div class="text">As our Organizational chart mention, we have an experienced and proved team to handle all recruitment work of any volume, successfully. There are two engineers as consultant to interview and identify candidates against client’s specific requirement. Each branch is equipped with latest communication tools and modern facilities. We maintain our data bank in computerizes way and have plan to apply customized software in this regard. Our operation team has come long way with their prompt and efficient activities.</div>
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
