
<template>
    <div class="tab">
        <button class="tablinks" @click="openForm(event, 'ChooseRole')">Choose Role</button>
        <button class="tablinks" @click="openForm(event, 'PersonalInformation')">Personal Information</button>
        <button class="tablinks" @click="openForm(event, 'OTPVerify')">OTP Verification</button>
        <button class="tablinks" @click="openForm(event, 'ServiceInformation')">Service Information</button>
        <button class="tablinks" @click="openForm(event, 'BankAccountDetails')">Bank Account Details</button>
        <button class="tablinks" @click="openForm(event, 'UploadDocuments')">Upload Documents</button>
    </div>
    <div id="ChooseRole" class="tabcontent">
        <div class="pickedrole">Picked: {{ formData.formrole }}</div>
        <div class="roles">
            <input type="radio" id="one" class="rolestyle" value="Freelancers" name="chooserole"
                v-model="formData.formrole" />
            <label for="one" class="rolelabels">Freelancers</label>

            <input type="radio" id="two" value="Business" class="rolestyle" name="chooserole"
                v-model="formData.formrole" />
            <label for="two" class="rolelabels">Business</label>
        </div>
    </div>
    <div id="PersonalInformation" class="tabcontent">
        <div class="form-group">
            <label for="fullName" class="labels">Full Name</label>
            <input type="text" class="form-control" placeholder="Enter your name" v-model="formData.fullName">
        </div>
        <div class="form-group">
            <label for="email" class="labels">Your Email</label>
            <input type="email" class="form-control" placeholder="Enter your email" v-model="formData.email">
        </div>
        <div class="form-group">
            <label for="phoneNumber" class="labels">Phone Number</label>
            <input type="number" class="form-control" placeholder="Enter your Phone Number"
                v-model="formData.phonenumber">
        </div>
        <div class="form-group">
            <label for="password" class="labels">Password</label>
            <input type="text" class="form-control" placeholder="Enter Password" v-model="formData.password">
        </div>
        <div class="form-group">
            <label for="idNumber" class="labels">ID Number</label>
            <input type="number" class="form-control" placeholder="Enter ID Number" v-model="formData.idnumber">
        </div>
        <div class="form-group" v-if="formData.formrole === 'Business'">
            <label for="companyName" class="labels">Company Name</label>
            <input type="text" class="form-control" placeholder="Enter Company Name" v-model="formData.companyname">
        </div>
        <div class="form-group" v-if="formData.formrole === 'Business'">
            <label for="companyName" class="labels">Commercial Registration Number</label>
            <input type="number" class="form-control" placeholder="Enter Commercial Registration Number"
                v-model="formData.commercialregnumber">
        </div>
    </div>
    <div id="OTPVerify" class="tabcontent">
        <div class="Otpdiv">
            <label class="Otp">Under Maintainence</label>
        </div>
    </div>
    <div id="ServiceInformation" class="tabcontent">
        <div class="form-group">
            <label for="serviceCategory" class="labels">Service Category</label>
            <select class="form-control" v-model="formData.servicecategory">
                <option value="opt1">Cleaning Services</option>
                <option>Furniture & Decor</option>
                <option>Maintainence Services</option>
                <option value="Other">Other</option>
            </select>
        </div>
        <div class="form-group" v-if="formData.servicecategory === 'Other'">
            <label for="servicecategory" class="labels">Enter Custom Service Category</label>
            <input type="text" class="form-control" placeholder="Start Writing Here..">
        </div>
        <div class="form-group">
            <label for="servicetoprovide" class="labels">Service to provide</label>
            <select class="form-control" v-model="formData.servicetoprovide">
                <option value="opt1">Cleaning Services</option>
                <option>Furniture & Decor</option>
                <option>Maintainence Services</option>
                <option value="Other">Other</option>
            </select>
        </div>
        <div class="form-group" v-if="formData.servicetoprovide === 'Other'">
            <label for="servicecategory" class="labels">Enter Custom Service to provide</label>
            <input type="text" class="form-control" placeholder="Start Writing Here..">
        </div>
        <div class="form-group">
            <label for="companyName" class="labels">Service Price</label>
            <input type="number" class="form-control" placeholder="Enter Service Price" v-model="formData.serviceprice">
        </div>
        <div class="form-group">
            <label class="filelabels">Upload Previous Work!</label>
            <input type="file" @change="uploadFile" ref="file" class="fileinput">
        </div>
    </div>
    <div id="BankAccountDetails" class="tabcontent">
        <div class="form-group">
            <label for="bankName" class="labels">Bank Name</label>
            <input type="text" class="form-control" placeholder="Enter Bank Name" v-model="formData.bankname">
        </div>
        <div class="form-group">
            <label for="accholderName" class="labels" v-if="formData.formrole === 'Freelancers'">Account Holder
                Name</label>
            <label for="accholderName" class="labels" v-else>Company Account Name</label>
            <input type="text" class="form-control" placeholder="Enter Account Name" v-model="formData.accholdername">
        </div>
        <div class="form-group">
            <label for="bankaccnumber" class="labels" v-if="formData.formrole === 'Freelancers'">Bank Account
                Number</label>
            <label for="accholderName" class="labels" v-else>Company Bank Account Number</label>

            <input type="number" class="form-control" placeholder="Enter Bank Account Number"
                v-model="formData.bankaccnumber">
        </div>
        <div class="form-group">
            <label for="bankIban" class="labels">IBAN</label>
            <input type="number" class="form-control" placeholder="Enter Bank IBAN" v-model="formData.Iban">
        </div>
    </div>
    <div id="UploadDocuments" class="tabcontent">

        <div class="form-group">
            <label class="filelabels">ID Document</label>
            <input type="file" @change="uploadFile" ref="file" class="fileinput">
        </div>
        <div class="form-group">
            <label class="filelabels">Stamped Personal Bank Account</label>
            <input type="file" @change="uploadFile" ref="file" class="fileinput">
        </div>
        <div class="form-group" v-if="formData.formrole === 'Business'">
            <label class="filelabels">Commercial Registeration</label>
            <input type="file" @change="uploadFile" ref="file" class="fileinput">
        </div>
        <div class="form-group-terms form-check">
            <input type="checkbox" class="form-check-input" v-model="formData.terms">
            <label class="form-check-label">I ACCEPT TERMS AND CONDITIONS</label>
        </div>
        <div class="btndiv">
            <button class="submitbtn" :disabled="!formData.terms">Submit Details</button>
        </div>
    </div>
</template>
<style>
.form-control {
    background-color: #D9D9D9 !important;
    border-radius: 20px !important;
    margin-left: 20px;
    width: 50% !important;

}

.form-group {
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-bottom: 20px;
    margin-top: 40px;
}

.form-group-terms {
    margin-bottom: 20px;
    margin-top: 40px;
    text-align: center;
    font-weight: bold;
}

.form-check-input {
    background-color: #D9D9D9;
    margin-right: 10px;
    color: #f4841f;
}

.labels {
    font-weight: bold;
    color: #f4841f
}

.filelabels {
    margin-right: 20px;
    font-weight: bold;
    color: #f4841f
}

.tab {
    overflow: hidden;
    width: 100%;
    border: 1px solid #ccc;
    background-color: #f4841f;
}

/* Style the buttons that are used to open the tab content */
.tab button {
    background-color: inherit;
    float: left;
    border: none;
    outline: none;
    cursor: pointer;
    padding: 14px 16px;
    transition: 0.3s;
    width: 16.6%;
    color: white;
    font-weight: bold;
    border-right: 2px solid white;
}

/* Change background color of buttons on hover */
.tab button:hover {
    background-color: #ddd;
}

/* Create an active/current tablink class */
.tab button.active {
    background-color: #ccc;
}

/* Style the tab content */
.tabcontent {
    display: none;
    padding: 6px 12px;
    border: 1px solid #ccc;
    border-top: none;
    width: 70%;
    margin: 0 auto;
    border: none;
}

.submitbtn {
    margin: 0 auto !important;
    width: 50%;
    border-radius: 20px;
    background-color: #f4841f;
    color: white;
    height: 30px;
}

.submitbtn:disabled {
    cursor: not-allowed;
    opacity: 0.8;
}

.btndiv {
    text-align: center;
    margin-bottom: 30px;
}

.pickedrole {
    font-weight: bold;
    text-align: center;
    margin-top: 100px;
    font-size: 50px;
    margin-bottom: 25px
}

.roles {
    text-align: center;
    margin-bottom: 100px
}

.rolelabels {
    font-weight: bold;
    font-size: 25px;
    color: #f4841f;
    margin-right: 20px;
    margin-left: 20px;
}

.rolestyle {
    color: #f4841f !important;
    height: 25px !important;
    width: 25px !important
}

.Otp {
    font-weight: bold;
    font-size: 50px;
    color: #f4841f
}

.Otpdiv {
    text-align: center;
    margin-top: 100px;
    margin-bottom: 100px;
}
</style>
<script>
// import { FormWizard, TabContent } from "vue-step-wizard";
// import "vue-step-wizard/dist/vue-step-wizard.css";
// import { required } from "vuelidate/lib/validators";
// import { email } from "vuelidate/lib/validators";
// import { numeric } from "vuelidate/lib/validators";
import { reactive } from 'vue'

export default {
    name: "StepFormValidation",
    components: {
    },
    //mixins: [ValidationHelper],
    data() {
        return {
            formData: {
                formrole: "",
                fullName: "",
                email: null,
                phonenumber: null,
                password: null,
                idnumber: null,
                companyname: null,
                commercialregnumber: null,
                servicecategory: 'opt1',
                servicetoprovide: 'opt1',
                serviceprice: null,
                bankname: null,
                accholdername: "",
                bankaccnumber: null,
                Iban: null,
                terms: false,
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
        },

        uploadFile() {
            this.Images = this.$refs.file.files[0];
        },
        submitFile() {
            const formData = new FormData();
            formData.append('file', this.Images);
            const headers = { 'Content-Type': 'multipart/form-data' };
            axios.post('https://httpbin.org/post', formData, { headers }).then((res) => {
                res.data.files; // binary representation of the file
                res.status; // HTTP status
            })
        },
        openForm(evt, cityName) {
            // Declare all variables
            var i, tabcontent, tablinks;

            // Get all elements with class="tabcontent" and hide them
            tabcontent = document.getElementsByClassName("tabcontent");
            for (i = 0; i < tabcontent.length; i++) {
                tabcontent[i].style.display = "none";
            }

            // Get all elements with class="tablinks" and remove the class "active"
            tablinks = document.getElementsByClassName("tablinks");
            for (i = 0; i < tablinks.length; i++) {
                tablinks[i].className = tablinks[i].className.replace(" active", "");
            }

            // Show the current tab, and add an "active" class to the button that opened the tab
            document.getElementById(cityName).style.display = "block";
            evt.currentTarget.className += " active";
        }
    }
}
</script>
