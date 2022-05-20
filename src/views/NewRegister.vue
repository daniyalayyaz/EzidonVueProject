
<template>
<div class="form-group">
        <label for="fullName">Full Name</label>
        <input
          type="text"
          class="form-control"
          placeholder="Enter your name"
          v-model="formData.fullName"
        >
      </div>
      <div class="form-group" >
        <label for="email">Your Email</label>
        <input
          type="email"
          class="form-control"
          placeholder="Enter your email"
          v-model="formData.email"
        >
      </div>
  <div class="form-group">
        <label for="phoneNumber">Phone Number</label>
        <input
          type="number"
          class="form-control"
          placeholder="Enter your Phone Number"
          v-model="formData.phonenumber"
        >
      </div>
      <div class="form-group">
        <label for="password">Password</label>
        <input
          type="text"
          class="form-control"
          placeholder="Enter Password"
          v-model="formData.password"
        >
      </div>
            <div class="form-group">
        <label for="idNumber">ID Number</label>
        <input
          type="number"
          class="form-control"
          placeholder="Enter ID Number"
          v-model="formData.idnumber"
        >
      </div>
            <div class="form-group">
        <label for="companyName">Company Name</label>
        <input
          type="text"
          class="form-control"
          placeholder="Enter Company Name"
          v-model="formData.companyname"
        >
      </div>
                 <div class="form-group">
        <label for="companyName">Commercial Registration Number</label>
        <input
          type="number"
          class="form-control"
          placeholder="Enter Commercial Registration Number"
          v-model="formData.commercialregnumber"
        >
      </div>
    <div class="form-group">
        <label for="serviceCategory">Service Category</label>
        <select
          class="form-control"
          v-model="formData.servicecategory"
        >
          <option selected>Cleaning Services</option>
          <option>Furniture & Decor</option>
          <option>Maintainence Services</option>
          <option>Other</option>
        </select>
      </div>
          <div class="form-group">
        <label for="servicetoprovide">Service to provide</label>
        <select
          class="form-control"
          v-model="formData.servicetoprovide"
        >
          <option>Cleaning Services</option>
          <option selected>Furniture & Decor</option>
          <option>Maintainence Services</option>
          <option>Other</option>
        </select>
      </div>
                      <div class="form-group">
        <label for="companyName">Service Price</label>
        <input
          type="number"
          class="form-control"
          placeholder="Enter Service Price"
          v-model="formData.serviceprice"
        >
      </div>
      <div class="form-group">
        <label for="bankName">Bank Name</label>
        <input
          type="text"
          class="form-control"
          placeholder="Enter Bank Name"
          v-model="formData.bankname"
        >
      </div>
      <div class="form-group">
        <label for="accholderName">Account Holder Name</label>
        <input
          type="text"
          class="form-control"
          placeholder="Enter Account Holder Name"
          v-model="formData.accholdername"
        >
      </div>
            <div class="form-group">
        <label for="bankaccnumber">Bank Account Number</label>
        <input
          type="number"
          class="form-control"
          placeholder="Enter Bank Account Number"
          v-model="formData.bankaccnumber"
        >
      </div>
                  <div class="form-group">
        <label for="bankIban">IBAN</label>
        <input
          type="number"
          class="form-control"
          placeholder="Enter Bank IBAN"
          v-model="formData.Iban"
        >
      </div>
      <div class="form-group form-check">
        <input
          type="checkbox"
          class="form-check-input"
          v-model="formData.terms"
        >
        <label class="form-check-label">I ACCEPT TERMS AND CONDITIONS</label>
      </div>
</template>
<style>
.form-control{
    background-color: #D9D9D9;
    border-radius: 20px;
    margin-left: 20px;
}
.form-group{
    display: flex;
    flex-direction: row;
    justify-content: center;
    margin-bottom: 20px;
}
.form-check-input{
    background-color: #D9D9D9;
    margin-right: 10px;
    color: #f4841f
}
</style>
<script>
// import { FormWizard, TabContent } from "vue-step-wizard";
// import "vue-step-wizard/dist/vue-step-wizard.css";
// import { required } from "vuelidate/lib/validators";
// import { email } from "vuelidate/lib/validators";
// import { numeric } from "vuelidate/lib/validators";

export default {
  name: "StepFormValidation",
  components: {
  },
  //mixins: [ValidationHelper],
  data() {
    return {
      formData: {
        fullName: "",
        email: null,
        phonenumber: null,
        password: null,
        idnumber: null,
        companyname: null,
        commercialregnumber: null,
        servicecategory: null,
        servicetoprovide: null,
        serviceprice:null,
        bankname: null,
        accholdername: "",
        bankaccnumber: null,
        Iban: null,
        terms: false
      },
    //   validationRules: [
    //     { fullName: { required }, email: { required, email } },
    //     { companyName: { required }, numberOfEmployees: { required, numeric } },
    //     { referral: { required }, terms: { required } }
    //   ]
    };
  },
  methods: {
    onComplete() {
      alert("Submitting Form ! Rock On");
    }
  }
};
</script>
