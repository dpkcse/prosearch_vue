<style scoped>
.from-table tbody tr td {
  padding-right: 2px;
  padding-bottom: 2px !important;
}

.from-table tbody tr {
  padding-bottom: 2px !important;
}
</style>

<script>
import axios from 'axios';
import {
  required,
  email,
  minLength,
  sameAs,
  maxLength,
  minValue,
  maxValue,
  numeric,
  url,
  alphaNum,
} from "vuelidate/lib/validators";

export default {
  name: "CurriculumPage",
  data() {
    return {
      status: "not_accepted",
      checkCustom: "not_accepted",
      checked: true,
      errors: null,
      form: {
        trade: '',
        country: '',
        name: '',
        f_name: '',
        m_name: '',
        nationality: '',
        dob: '',
        pob: '',
        religion: '',
        marital_status: '',
        height: '',
        weight: '',
        present_address: '',
        permanent_address: '',
        candidate_number: '',
        family_number: '',
        passport_no: '',
        place_of_issue: '',
        issue_date: '',
        expire_date: '',
        academicqalification: '',
        passport_number: '',
        issue_place: '',
        highest_edu: '',
        skill_training: '',
        language_training: '',
        years: '',
        company_name: '',
        position: '',
        from: '',
        to: '',
        english: '',
        bangla: '',
        arabic: '',
        hindi: '',
        urdu: '',
        japanese: '',
        others: '',
        professional_country: [],
        professional_year: [],
        professional_company_name: [],
        professional_position: [],
        professional_from: [],
        professional_to: [],
      },
      submitform: false,
      submitted: false,
      success_message: '',
      total_professional: [0, 1, 2]
    };
  },
  validations: {
    form: {
      trade: {
        required,
      },
      last_name: {
        required,
      },
      gender: {
        required,
      },
      email: {
        required,
      },
      country_code: {
        required,
      },
      country: {
        required,
      },
      phone_code: {
        required,
      },
      phone_number: {
        required,
      },
      password: {
        required,
      },
      password_confirmation: {
        required,
      },
    },
  },

  methods: {
    formSubmit(event) {
      event.preventDefault();
      this.submitted = false;
      let passport_image = this.$refs.passport_image.files[0];
      let user_photo = this.$refs.user_photo.files[0];
      let education_certificate = this.$refs.education_certificate.files[0];
      let experience_certificate = this.$refs.experience_certificate.files[0];
      let lan_course_certificate = this.$refs.lan_course_certificate.files[0];
      let police_clearance = this.$refs.police_clearance.files[0];
      let skill_training_certificate = this.$refs.skill_training_certificate.files[0];
      let medical_card = this.$refs.medical_card.files[0];
      let job_test = this.$refs.job_test.files[0];

      let form = new FormData();
      form.append('trade', this.form.trade);
      form.append('country', this.form.country);
      form.append('name', this.form.name);
      form.append('f_name', this.form.f_name);
      form.append('m_name', this.form.m_name);
      form.append('nationality', this.form.nationality);
      form.append('dob', this.form.dob);
      form.append('pob', this.form.pob);
      form.append('religion', this.form.religion);
      form.append('marital_status', this.form.marital_status);
      form.append('height', this.form.height);
      form.append('weight', this.form.weight);
      form.append('weight', this.form.weight);
      form.append('present_address', this.form.present_address);
      form.append('permanent_address', this.form.permanent_address);
      form.append('candidate_number', this.form.candidate_number);
      form.append('family_number', this.form.family_number);
      form.append('passport_no', this.form.passport_no);
      form.append('place_of_issue', this.form.place_of_issue);
      form.append('issue_date', this.form.issue_date);
      form.append('expire_date', this.form.expire_date);
      form.append('academicqalification', this.form.academicqalification);
      form.append('passport_number', this.form.passport_number);
      form.append('issue_place', this.form.issue_place);
      form.append('highest_edu', this.form.highest_edu);
      form.append('skill_training', this.form.skill_training);
      form.append('language_training', this.form.language_training);

      form.append('pro_country', this.form.professional_country);
      form.append('years', this.form.professional_year);
      form.append('company_name', this.form.professional_company_name);
      form.append('position', this.form.professional_position);
      form.append('from', this.form.professional_from);
      form.append('to', this.form.professional_to);

      form.append('english', this.form.english);
      form.append('bangla', this.form.bangla);
      form.append('arabic', this.form.arabic);
      form.append('hindi', this.form.hindi);
      form.append('japanese', this.form.japanese);
      form.append('others', this.form.others);

      form.append('passport', passport_image);
      form.append('photo', user_photo);
      form.append('education', education_certificate);
      form.append('experience', experience_certificate);
      form.append('langu', lan_course_certificate);
      form.append('police', police_clearance);
      form.append('skill', skill_training_certificate);
      form.append('medical', medical_card);
      form.append('idcard', job_test);
      axios

        .post("http://127.0.0.1:8000/api/make-cv", form)
        .then((response) => {
          console.log(response.data.satus_code);
          if (response.data.satus_code == 200) {
            this.success_message = "Successfully saved."
            this.resetForm();
            this.form.trade = '';
            this.$v.form = {};
            this.$refs.cvForm.reset();

          } else {
            var str = response.data.message;
            this.success_message = "Something wrong"
            var jsonParse = JSON.parse(str);
            this.errorCheck(jsonParse);
          }
        })
        .catch((error) => {
          if (error.response != undefined) {
            this.errors = error.response.data.errors;
          }
        });
    },
    errorCheck(obj) {
      if (obj.error) {
        this.errors = obj.message;
      } else if (obj.message == "Token has expired") {
        this.$router.push({name: "logout"});
      } else if (
        obj.message !== "Token has expired" &&
        obj.message !== "The given data was invalid."
      ) {
        this.errors = obj.message;
      } else if (obj.message == "The given data was invalid.") {
        this.errors = obj.errors;
      } else {
        this.flashMessage.show({
          time: 5000,
          status: "error",
          title: "Error",
          message: "Problem in data save",
        });
      }
    },
    resetForm(event) {
      console.log("Reseting the form");
      event.target.reset();
    },
  },
}
</script>

<template>
  <section class="contact-section">
    <div class="auto-container">
      <div class="sec-title centered">
        <h2>Send Your CV <span class="dot">.</span></h2>
      </div>

      <div class="upper-info">
        <div class="row clearfix">
          <div class="info-block col-xl-3 col-lg-6 col-md-6 col-sm-12 wow fadeInUp" data-wow-delay="0ms"
               data-wow-duration="1500ms">
            <div class="inner-box">
              <h5>PROSEARCH RECRUITMENT CONSULTANTS</h5>
              <div class="text">
                <ul class="contact-info">
                  <li class="address"><span class="icon flaticon-pin-1"></span> City Heart (13th floor), Suite-07, 67
                    Naya paltan, Dhaka-1000
                  </li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 02 9344102">TEL : +88 02 8332935</a></li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 02 9344102">TEL : +88 02 22222402</a>
                  </li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 01817094118">Mobile: +880 1634-322006</a>
                  </li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 01817094118">Mobile: +880 1787-662924</a>
                  </li>
                  <li><span class="icon flaticon-email-2"></span><a href="mailto:modern_brs@yahoo.com">prosearchtc@gmail.com</a>
                  </li>
                  <li><span class="icon flaticon-email-2"></span><a href="mailto:rdronidhaka@gmail.com">rdronidhaka@gmail.com</a>
                  </li>
                </ul>
              </div>
            </div>
          </div>

          <div class="info-block col-xl-9 col-lg-6 col-md-6 col-sm-12 wow fadeInUp" data-wow-delay="900ms"
               data-wow-duration="1500ms">
            <div class="default-form">
              <div class="alert alert-success" role="alert" v-if="success_message">
                {{ success_message }}
              </div>
              <form class="needs-validation" ref="cvForm" v-on:submit.prevent="formSubmit">
                <div class="row clearfix">
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="trade"
                        v-model="form.trade"
                        name="trade"
                        type="text"
                        class="form-control"
                        placeholder="Type Trade Type"
                        required
                        value
                        :class="{ 'is-invalid': submitted && $v.form.trade.$error }"
                      />

                    </div>
                    <div v-if="submitted && $v.form.trade.$error" class="invalid-feedback">
                      <span v-if="!$v.form.trade.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="country"
                        v-model="form.country"
                        name="country"
                        type="text"
                        class="form-control"
                        placeholder="Type Country (Interested For)"
                        value
                        :class="{ 'is-invalid': submitted && $v.form.country.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.country.$error" class="invalid-feedback">
                      <span v-if="!$v.form.country.required">This value is required.</span>
                    </div>
                  </div>
                  <h5 class="form-group col-lg-12 col-md-12 col-sm-12">Personal Information</h5>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="name"
                        v-model="form.name"
                        name="name"
                        type="text"
                        class="form-control"
                        placeholder="Type Name"
                        value
                        :class="{ 'is-invalid': submitted && $v.form.name.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.name.$error" class="invalid-feedback">
                      <span v-if="!$v.form.name.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="fname"
                        v-model="form.f_name"
                        name="fname"
                        type="text"
                        class="form-control"
                        placeholder="Type Father's Name"
                        value
                        :class="{ 'is-invalid': submitted && $v.form.fname.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.f_name.$error" class="invalid-feedback">
                      <span v-if="!$v.form.f_name.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="fname"
                        v-model="form.m_name"
                        name="mname"
                        type="text"
                        class="form-control"
                        placeholder="Type Mother's Name"
                        value
                        :class="{ 'is-invalid': submitted && $v.form.m_name.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.m_name.$error" class="invalid-feedback">
                      <span v-if="!$v.form.m_name.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="nationality"
                        v-model="form.nationality"
                        name="nationality"
                        type="text"
                        placeholder="Nationality"
                        class="form-control"
                        value="BANGLADESHI"
                        :class="{ 'is-invalid': submitted && $v.form.nationality.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.nationality.$error" class="invalid-feedback">
                      <span v-if="!$v.form.nationality.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="dob"
                        v-model="form.dob"
                        name="dob"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Date of birth"
                        :class="{ 'is-invalid': submitted && $v.form.dob.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.dob.$error" class="invalid-feedback">
                      <span v-if="!$v.form.dob.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="pob"
                        v-model="form.pob"
                        name="pob"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Place of birth"
                        :class="{ 'is-invalid': submitted && $v.form.pob.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.pob.$error" class="invalid-feedback">
                      <span v-if="!$v.form.pob.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <select class="form-select" aria-label="Default select example"
                              id="religion"
                              v-model="form.religion"
                              name="religion"
                              :class="{ 'is-invalid': submitted && $v.form.religion.$error }">
                        <option value="#">Select Religion</option>
                        <option value="Islam">Islam</option>
                        <option value="Hinduism">Hinduism</option>
                        <option value="Buddhism">Buddhism</option>
                        <option value="Christianity">Christianity</option>
                        <option value="Other">Other</option>
                      </select>
                    </div>
                    <div v-if="submitted && $v.form.religion.$error" class="invalid-feedback">
                      <span v-if="!$v.form.religion.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <select class="form-select" aria-label="Default select example" id="marital_status"
                              v-model="form.marital_status"
                              name="marital_status"
                              :class="{ 'is-invalid': submitted && $v.form.marital_status.$error }">
                        <option value="#">Marital Status</option>
                        <option value="Married">Married</option>
                        <option value="Unmarried">Unmarried</option>
                      </select>
                    </div>
                    <div v-if="submitted && $v.form.marital_status.$error" class="invalid-feedback">
                      <span v-if="!$v.form.marital_status.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="height"
                        v-model="form.height"
                        name="height"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Your Height"
                        :class="{ 'is-invalid': submitted && $v.form.height.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.height.$error" class="invalid-feedback">
                      <span v-if="!$v.form.height.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="weight"
                        v-model="form.weight"
                        name="weight"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Your Weight"
                        :class="{ 'is-invalid': submitted && $v.form.weight.$error }"
                      />
                    </div>
                  </div>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <textarea id="present_address"
                                v-model="form.present_address"
                                name="present_address"
                                class="form-control"
                                value
                                placeholder="Permanent Address"
                                :class="{ 'is-invalid': submitted && $v.form.present_address.$error }"></textarea>
                    </div>
                  </div>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <textarea id="permanent_address"
                                v-model="form.permanent_address"
                                name="permanent_address"
                                class="form-control"
                                value
                                placeholder="Permanent Address"
                                :class="{ 'is-invalid': submitted && $v.form.permanent_address.$error }"></textarea>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="candidate_number"
                        v-model="form.candidate_number"
                        name="candidate_number"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Candidate Number"
                        :class="{ 'is-invalid': submitted && $v.form.candidate_number.$error }"
                      />
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="family_number"
                        v-model="form.family_number"
                        name="family_number"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Family Number"
                        :class="{ 'is-invalid': submitted && $v.form.family_number.$error }"
                      />
                    </div>
                  </div>

                  <h5 class="form-group col-lg-12 col-md-12 col-sm-12">Passport Information</h5>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="passport_no"
                        v-model="form.passport_number"
                        name="passport_no"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Passport Number"
                        :class="{ 'is-invalid': submitted && $v.form.passport_number.$error }"
                      />
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="place_of_issue"
                        v-model="form.issue_place"
                        name="place_of_issue"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Place of issue"
                        :class="{ 'is-invalid': submitted && $v.form.issue_place.$error }"
                      />
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="issue_date"
                        v-model="form.issue_date"
                        name="issue_date"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Issue Date"
                        :class="{ 'is-invalid': submitted && $v.form.issue_date.$error }"
                      />
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="expire_date"
                        v-model="form.expire_date"
                        name="expire_date"
                        type="text"
                        class="form-control"
                        value
                        placeholder="Expire Date"
                        :class="{ 'is-invalid': submitted && $v.form.expire_date.$error }"
                      />
                    </div>
                  </div>
                  <h5 class="form-group col-lg-12 col-md-12 col-sm-12">Academic Qualification</h5>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="form-check form-check-inline">
                      <input
                        v-model="form.highest_edu"
                        name="academicqalification"
                        type="radio"
                        class="form-check-input"
                        value="SCHOOL"
                        placeholder="Expire Date"
                        :class="{ 'is-invalid': submitted && $v.form.highest_edu.$error }"
                      />
                      <label class="form-check-label" for="SCHOOL">SCHOOL</label>
                    </div>
                    <div class="form-check form-check-inline">
                      <input
                        v-model="form.highest_edu"
                        name="academicqalification"
                        type="radio"
                        class="form-check-input"
                        value="SSC"
                        placeholder="Expire Date"
                        :class="{ 'is-invalid': submitted && $v.form.highest_edu.$error }"
                      />
                      <label class="form-check-label" for="SSC">SSC</label>
                    </div>
                    <div class="form-check form-check-inline">
                      <input
                        v-model="form.highest_edu"
                        name="academicqalification"
                        type="radio"
                        class="form-check-input"
                        value="HSC"
                        placeholder="Expire Date"
                        :class="{ 'is-invalid': submitted && $v.form.highest_edu.$error }"
                      />
                      <label class="form-check-label" for="HSC">HSC</label>
                    </div>
                    <div class="form-check form-check-inline">
                      <input
                        v-model="form.highest_edu"
                        name="academicqalification"
                        type="radio"
                        class="form-check-input"
                        value="GRADUATION"
                        placeholder="Expire Date"
                        :class="{ 'is-invalid': submitted && $v.form.highest_edu.$error }"
                      />
                      <label class="form-check-label" for="GRADUATION">GRADUATION</label>
                    </div>
                    <div class="form-check form-check-inline">
                      <input
                        v-model="form.highest_edu"
                        name="academicqalification"
                        type="radio"
                        class="form-check-input"
                        value="POSTGRADUATION"
                        placeholder="Expire Date"
                        :class="{ 'is-invalid': submitted && $v.form.highest_edu.$error }"
                      />
                      <label class="form-check-label" for="POSTGRADUATION">POST-GRADUATION</label>
                    </div>
                    <div class="form-check form-check-inline">
                      <input
                        v-model="form.highest_edu"
                        name="academicqalification"
                        type="radio"
                        class="form-check-input"
                        value="OTHERS"
                        placeholder="Expire Date"
                        :class="{ 'is-invalid': submitted && $v.form.highest_edu.$error }"
                      />
                      <label class="form-check-label" for="OTHERS">OTHERS</label>
                    </div>
                  </div>
                  <h5 class="form-group col-lg-12 col-md-12 col-sm-12">Professional Qualification</h5>
                  <div class="form-group col-lg-12 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <table class="from-table">
                        <thead>
                        <tr>
                          <th>Country</th>
                          <th>Years</th>
                          <th>Company Name</th>
                          <th>Position</th>
                          <th>From</th>
                          <th>To</th>
                        </tr>
                        </thead>
                        <tbody>
                        <tr v-for="(pro, index) in total_professional" :key="index">
                          <td>
                            <input
                              id="coutntry1"
                              v-model="form.professional_country[pro]"
                              name="coutntry[]"
                              type="text"
                              class="form-control"
                              value
                              placeholder="1"
                              :class="{ 'is-invalid': submitted && $v.form.professional_country.$error }"
                            />
                          </td>
                          <td>
                            <input
                              id="year1"
                              v-model="form.professional_year[pro]"
                              name="year[]"
                              type="text"
                              class="form-control"
                              value
                              :class="{ 'is-invalid': submitted && $v.form.professional_year.$error }"
                            />
                          </td>
                          <td>
                            <input
                              id="cname1"
                              v-model="form.professional_company_name[pro]"
                              name="cname[]"
                              type="text"
                              class="form-control"
                              value
                              :class="{ 'is-invalid': submitted && $v.form.professional_company_name.$error }"
                            />
                          </td>
                          <td>
                            <input
                              id="position1"
                              v-model="form.professional_position[pro]"
                              name="position[]"
                              type="text"
                              class="form-control"
                              value
                              :class="{ 'is-invalid': submitted && $v.form.professional_position.$error }"
                            />
                          </td>
                          <td>
                            <input
                              id="from1"
                              v-model="form.professional_from[pro]"
                              name="from[]"
                              type="text"
                              class="form-control"
                              value
                              :class="{ 'is-invalid': submitted && $v.professional_from.pex.$error }"
                            />
                          </td>
                          <td>
                            <input
                              id="to1"
                              v-model="form.professional_to[pro]"
                              name="to[]"
                              type="text"
                              class="form-control"
                              value
                              :class="{ 'is-invalid': submitted && $v.form.professional_to.$error }"
                            />
                          </td>
                        </tr>
                        </tbody>
                      </table>
                    </div>
                  </div>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                        <textarea id="skill_training"
                                  v-model="form.skill_training"
                                  name="skill_training"
                                  class="form-control"
                                  value
                                  placeholder="Skill Training Course"
                                  :class="{ 'is-invalid': submitted && $v.form.skill_training.$error }"></textarea>
                    </div>
                  </div>
                  <h5 class="form-group col-lg-12 col-md-12 col-sm-12">Language Known</h5>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <table class="table table-bordered">
                        <thead>
                        <tr>
                          <th class="text-center">ENGLISH</th>
                          <th class="text-center">BANGLA</th>
                          <th class="text-center">ARABIC</th>
                          <th class="text-center">HINDI</th>
                          <th class="text-center">URDU</th>
                          <th class="text-center">JAPANESE</th>
                          <th class="text-center">OTHERS</th>
                        </tr>
                        </thead>
                        <tbody>
                        <tr>
                          <td class="text-center">
                            <input
                              id="ENGLISH"
                              v-model="form.english"
                              name="language"
                              class="form-control"
                              type="checkbox"
                              value="ENGLISH"
                              :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                            /></td>
                          <td class="text-center">
                            <input
                              id="BANGLA"
                              v-model="form.bangla"
                              name="language"
                              class="form-control"
                              type="checkbox"
                              value="BANGLA"
                              :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                            /></td>
                          <td class="text-center">
                            <input
                              id="ARABIC"
                              v-model="form.arabic"
                              name="language"
                              class="form-control"
                              type="checkbox"
                              value="ARABIC"
                              :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                            /></td>
                          <td class="text-center">
                            <input
                              id="HINDI"
                              v-model="form.hindi"
                              name="language"
                              class="form-control"
                              type="checkbox"
                              value="HINDI"
                              :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                            /></td>
                          <td class="text-center">
                            <input
                              id="URDU"
                              v-model="form.urdu"
                              name="language"
                              class="form-control"
                              type="checkbox"
                              value="URDU"
                              :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                            /></td>
                          <td class="text-center">
                            <input
                              id="JAPANESE"
                              v-model="form.japanese"
                              name="language"
                              class="form-control"
                              type="checkbox"
                              value="JAPANESE"
                              :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                            /></td>
                          <td class="text-center">
                            <input
                              id="OTHERS"
                              v-model="form.others"
                              name="language"
                              class="form-control"
                              type="checkbox"
                              value="OTHERS"
                              :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                            />
                          </td>
                        </tr>
                        </tbody>
                      </table>
                    </div>
                  </div>

                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <textarea type="text" name="trade" v-model="form.language_training" value="" rows="3"
                                placeholder="Language Training Course"></textarea>
                    </div>
                  </div>
                  <h5 class="form-group col-lg-12 col-md-12 col-sm-12">Enclose</h5>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <table class="table table-bordered">
                        <tbody>
                        <tr class="align-middle">
                          <td class="align-middle">1</td>
                          <td class="align-middle">Passport Copy</td>
                          <td class="text-center">
                            <input type="file" accept="application/pdf, image/jpeg, image/jpg" ref="passport_image"
                                   required="">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">2</td>
                          <td class="align-middle">Photo</td>
                          <td class="text-center">
                            <input type="file" ref="user_photo" accept="application/pdf, image/jpeg, image/jpg"
                                   required="">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">3</td>
                          <td class="align-middle">Education Certificate Copy</td>
                          <td class="text-center">
                            <input type="file" ref="education_certificate"
                                   accept="application/pdf, image/jpeg, image/jpg"
                                   required="">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">4</td>
                          <td class="align-middle">Experience Certificate Copy</td>
                          <td class="text-center">
                            <input type="file" ref="experience_certificate"
                                   accept="application/pdf, image/jpeg, image/jpg"
                                   required="">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">5</td>
                          <td class="align-middle">Language Course Certificate Copy</td>
                          <td class="text-center">
                            <input type="file" ref="lan_course_certificate"
                                   accept="application/pdf, image/jpeg, image/jpg">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">6</td>
                          <td class="align-middle">Police Clearance Copy</td>
                          <td class="text-center">
                            <input type="file" ref="police_clearance" accept="application/pdf, image/jpeg, image/jpg">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">7</td>
                          <td class="align-middle">Skill Training Certificate Copy</td>
                          <td class="text-center">
                            <input type="file" ref="skill_training_certificate"
                                   accept="application/pdf, image/jpeg, image/jpg">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">8</td>
                          <td class="align-middle">Medical Card Copy</td>
                          <td class="text-center">
                            <input type="file" ref="medical_card" accept="application/pdf, image/jpeg, image/jpg">
                          </td>
                        </tr>
                        <tr class="align-middle">
                          <td class="align-middle">9</td>
                          <td class="align-middle">Job Test Copy</td>
                          <td class="text-center">
                            <input type="file" ref="job_test" accept="application/pdf, image/jpeg, image/jpg"
                                   required=""></td>
                        </tr>
                        </tbody>
                      </table>
                    </div>
                  </div>

                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <button class="theme-btn btn-style-one" type="submit"><i class="btn-curve"></i> <span
                      class="btn-title">Submit</span></button>
                    <!-- <button  type="submit" class="theme-btn btn-style-one">
                      <i class="btn-curve"></i>
                      <span class="btn-title">Submit</span>
                    </button> -->
                  </div>
                </div>
              </form>
            </div>
          </div>
        </div>
      </div>
    </div>

  </section>
</template>

