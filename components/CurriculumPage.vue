<style scoped>
  .from-table tbody tr td{
    padding-right: 2px;
    padding-bottom: 2px !important;
  }
  .from-table tbody tr{
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
              trade: "",
              last_name: "",
              gender: "",
              email: "",
              country_code: "",
              country: "",
              phone_code: "",
              phone_number: "",
              password: "",
              password_confirmation: "",
            },
            submitform: false,
            submitted: false,
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
            console.log(event);
            this.submitted = true;
            this.$v.$touch();
            axios
              .post("http://localhost/admin/cv/post/", {
                first_name: this.form.first_name,
                last_name: this.form.last_name,
                gender: this.form.gender,
                email: this.form.email,
                country_code: this.form.country_code,
                country: this.form.country,
                phone_code: this.form.phone_code,
                phone_number: this.form.phone_number,
                password: this.form.password,
                password_confirmation: this.form.password_confirmation,
                accessToken: localStorage.getItem("access_tocken"),
              })
              .then((response) => {
                if (response.data.status) {
                  this.$refs.cvForm.reset();
                  this.$router.push({ name: "all_admin" });
                } else {
                  var str = response.data.message;
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
              this.$router.push({ name: "logout" });
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
        <h2>Send Your CV<span class="dot">.</span></h2>
      </div>

      <div class="upper-info">
        <div class="row clearfix">
          <div class="info-block col-xl-3 col-lg-6 col-md-6 col-sm-12 wow fadeInUp" data-wow-delay="0ms"
               data-wow-duration="1500ms">
            <div class="inner-box">
              <h5>PROSEARCH RECRUITMENT CONSULTANTS</h5>
              <div class="text">
                <ul class="contact-info">
                  <li class="address"><span class="icon flaticon-pin-1"></span> City Heart (13th floor), Suite-07, 67 Naya paltan, Dhaka-1000</li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 02 9344102">TEL : +88 02 8332935</a></li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 02 9344102">TEL : +88 02 22222402</a></li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 01817094118">Mobile: +880 1634-322006</a></li>
                  <li><span class="icon flaticon-call"></span><a href="tel:+88 01817094118">Mobile: +880 1787-662924</a></li>
                  <li><span class="icon flaticon-email-2"></span><a href="mailto:modern_brs@yahoo.com">prosearchtc@gmail.com</a></li>
                  <li><span class="icon flaticon-email-2"></span><a href="mailto:rdronidhaka@gmail.com">rdronidhaka@gmail.com</a></li>
                </ul>
              </div>
            </div>
          </div>

          <div class="info-block col-xl-9 col-lg-6 col-md-6 col-sm-12 wow fadeInUp" data-wow-delay="900ms" data-wow-duration="1500ms">
            <div class="default-form">
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
                        v-model="form.fname"
                        name="fname"
                        type="text"
                        class="form-control"
                        placeholder="Type Father's Name"
                        value
                        :class="{ 'is-invalid': submitted && $v.form.fname.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.fname.$error" class="invalid-feedback">
                      <span v-if="!$v.form.fname.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="fname"
                        v-model="form.mname"
                        name="mname"
                        type="text"
                        class="form-control"
                        placeholder="Type Mother's Name"
                        value
                        :class="{ 'is-invalid': submitted && $v.form.mname.$error }"
                      />
                    </div>
                    <div v-if="submitted && $v.form.mname.$error" class="invalid-feedback">
                      <span v-if="!$v.form.mname.required">This value is required.</span>
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="nationality"
                        v-model="form.nationality"
                        name="nationality"
                        type="text"
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
                        v-model="form.passport_no"
                        name="passport_no"
                        type="text"
                        class="form-control"
                        value                        
                        placeholder="Passport Number"
                        :class="{ 'is-invalid': submitted && $v.form.passport_no.$error }"
                      />
                    </div>
                  </div>
                  <div class="form-group col-lg-6 col-md-6 col-sm-12">
                    <div class="field-inner">
                      <input
                        id="place_of_issue"
                        v-model="form.place_of_issue"
                        name="place_of_issue"
                        type="text"
                        class="form-control"
                        value                        
                        placeholder="Place of issue"
                        :class="{ 'is-invalid': submitted && $v.form.place_of_issue.$error }"
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
                          v-model="form.academicqalification"
                          name="academicqalification"
                          type="radio"
                          class="form-check-input"
                          value="SCHOOL"                        
                          placeholder="Expire Date"
                          :class="{ 'is-invalid': submitted && $v.form.academicqalification.$error }"
                        />
                        <label class="form-check-label" for="SCHOOL">SCHOOL</label>
                    </div>
                    <div class="form-check form-check-inline">
                        <input
                          v-model="form.academicqalification"
                          name="academicqalification"
                          type="radio"
                          class="form-check-input"
                          value="SSC"                        
                          placeholder="Expire Date"
                          :class="{ 'is-invalid': submitted && $v.form.academicqalification.$error }"
                        />
                        <label class="form-check-label" for="SSC">SSC</label>
                    </div>
                    <div class="form-check form-check-inline">
                        <input
                          v-model="form.academicqalification"
                          name="academicqalification"
                          type="radio"
                          class="form-check-input"
                          value="HSC"                        
                          placeholder="Expire Date"
                          :class="{ 'is-invalid': submitted && $v.form.academicqalification.$error }"
                        />
                        <label class="form-check-label" for="HSC">HSC</label>
                    </div>
                    <div class="form-check form-check-inline">
                        <input
                          v-model="form.academicqalification"
                          name="academicqalification"
                          type="radio"
                          class="form-check-input"
                          value="GRADUATION"                        
                          placeholder="Expire Date"
                          :class="{ 'is-invalid': submitted && $v.form.academicqalification.$error }"
                        />
                        <label class="form-check-label" for="GRADUATION">GRADUATION</label>
                    </div>
                    <div class="form-check form-check-inline">
                        <input
                          v-model="form.academicqalification"
                          name="academicqalification"
                          type="radio"
                          class="form-check-input"
                          value="POSTGRADUATION"                        
                          placeholder="Expire Date"
                          :class="{ 'is-invalid': submitted && $v.form.academicqalification.$error }"
                        />
                        <label class="form-check-label" for="POSTGRADUATION">POST-GRADUATION</label>
                    </div>
                    <div class="form-check form-check-inline">
                        <input
                          v-model="form.academicqalification"
                          name="academicqalification"
                          type="radio"
                          class="form-check-input"
                          value="OTHERS"                        
                          placeholder="Expire Date"
                          :class="{ 'is-invalid': submitted && $v.form.academicqalification.$error }"
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
                          <tr>
                            <td>
                              <input
                                id="coutntry1"
                                v-model="form.coutntry"
                                name="coutntry[]"
                                type="text"
                                class="form-control"
                                value                        
                                placeholder="1"
                                :class="{ 'is-invalid': submitted && $v.form.coutntry.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="year1"
                                v-model="form.year"
                                name="year[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.year.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="cname1"
                                v-model="form.cname"
                                name="cname[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.cname.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="position1"
                                v-model="form.position"
                                name="position[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.position.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="from1"
                                v-model="form.from"
                                name="from[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.from.pex.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="to1"
                                v-model="form.to"
                                name="to[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.to.$error }"
                              />
                            </td>
                          </tr>
                          <tr>
                            <td>
                              <input
                                id="coutntry2"
                                v-model="form.coutntry"
                                name="coutntry[]"
                                type="text"
                                class="form-control"
                                value                        
                                placeholder="2"
                                :class="{ 'is-invalid': submitted && $v.form.coutntry.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="year2"
                                v-model="form.year"
                                name="year[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.year.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="cname2"
                                v-model="form.cname"
                                name="cname[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.cname.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="position2"
                                v-model="form.position"
                                name="position[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.position.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="from2"
                                v-model="form.from"
                                name="from[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.from.pex.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="to2"
                                v-model="form.to"
                                name="to[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.to.$error }"
                              />
                            </td>
                          </tr>
                          <tr>
                            <td>
                              <input
                                id="coutntry3"
                                v-model="form.coutntry"
                                name="coutntry[]"
                                type="text"
                                class="form-control"
                                value                        
                                placeholder="3"
                                :class="{ 'is-invalid': submitted && $v.form.coutntry.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="year3"
                                v-model="form.year"
                                name="year[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.year.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="cname3"
                                v-model="form.cname"
                                name="cname[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.cname.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="position3"
                                v-model="form.position"
                                name="position[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.position.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="from3"
                                v-model="form.from"
                                name="from[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.from.pex.$error }"
                              />
                            </td>
                            <td>
                              <input
                                id="to3"
                                v-model="form.to"
                                name="to[]"
                                type="text"
                                class="form-control"
                                value
                                :class="{ 'is-invalid': submitted && $v.form.to.$error }"
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
                                v-model="form.language"
                                name="language"
                                class="form-control"
                                type="checkbox" 
                                value="ENGLISH"
                                :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                              /></td>
                            <td class="text-center">
                              <input
                                id="BANGLA"
                                v-model="form.language"
                                name="language"
                                class="form-control"
                                type="checkbox" 
                                value="BANGLA"
                                :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                              /></td>
                            <td class="text-center">
                              <input
                                id="ARABIC"
                                v-model="form.language"
                                name="language"
                                class="form-control"
                                type="checkbox" 
                                value="ARABIC"
                                :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                              /></td>
                            <td class="text-center">
                              <input
                                id="HINDI"
                                v-model="form.language"
                                name="language"
                                class="form-control"
                                type="checkbox" 
                                value="HINDI"
                                :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                              /></td>
                            <td class="text-center">
                              <input
                                id="URDU"
                                v-model="form.language"
                                name="language"
                                class="form-control"
                                type="checkbox" 
                                value="URDU"
                                :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                              /></td>
                            <td class="text-center">
                              <input
                                id="ENGJAPANESELISH"
                                v-model="form.language"
                                name="language"
                                class="form-control"
                                type="checkbox" 
                                value="JAPANESE"
                                :class="{ 'is-invalid': submitted && $v.form.language.$error }"
                              /></td>
                            <td class="text-center">
                              <input
                                id="OTHERS"
                                v-model="form.language"
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
                        <textarea type="text" name="trade" value="" rows="3" placeholder="Language Training Course" ></textarea>
                      </div>
                  </div>
                  <h5 class="form-group col-lg-12 col-md-12 col-sm-12">Enclose</h5>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <div class="field-inner">
                      <table class="table table-bordered">
                        <tbody>
                          <tr class="align-middle">
                            <td class="align-middle">1</td><td class="align-middle">Passport Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" required=""></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">2</td><td class="align-middle">Photo</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" required=""></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">3</td><td class="align-middle">Education Certificate Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" required=""></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">4</td><td class="align-middle">Experience Certificate Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" required=""></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">5</td><td class="align-middle">Language Course Certificate Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" ></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">6</td><td class="align-middle">Police Clearance Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" ></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">7</td><td class="align-middle">Skill Training Certificate Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" ></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">8</td><td class="align-middle">Medical Card Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" ></td>
                          </tr>
                          <tr class="align-middle">
                            <td class="align-middle">9</td><td class="align-middle">Job Test Copy</td><td class="text-center"><input type="file" accept = "application/pdf, image/jpeg, image/jpg" required=""></td>
                          </tr>
                        </tbody>
                      </table>
                    </div>
                  </div>
                  <div class="form-group col-lg-12 col-md-12 col-sm-12">
                    <button class="theme-btn btn-style-one" type="submit"> <i class="btn-curve"></i> <span class="btn-title">Submit</span></button>
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

