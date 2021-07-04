<template>
<div class="row">
    <div class="col-xl-9 mx-auto">
        
        <hr>
        <div class="card border-top border-0 border-4 border-info">
            <div class="card-body">
                <div class="border p-4 rounded">
                    <div class="card-title d-flex align-items-center">
                        <div><i class="bx bxs-user me-1 font-22 text-info"></i>
                        </div>
                        <h5 class="mb-0 text-info">User Registration</h5>
                    </div>
                    <hr>
                    <form @submit.prevent = "submitForm">
                    <div class="row mb-3">
                        <label for="inputEnterYourName" class="col-sm-3 col-form-label">Enter Your Name</label>
                        <div class="col-sm-9">
                            <input type="text" class="form-control" id="inputEnterYourName" placeholder="Enter Your Name" v-model="name">
                            <span v-if="(!$v.name.required || $v.name.$dirty)" class="text-danger">Name is required</span>
                            <span v-if="!$v.name.alpha || $v.name.$dirty" class="text-danger">Name should only contain alphabets</span>
                        </div>
                    </div>
                    <div class="row mb-3">
                        <label for="inputPhoneNo2" class="col-sm-3 col-form-label">Phone No</label>
                        
                        <div class="col-sm-9">
                            <input type="number" class="form-control" id="inputPhoneNo2" placeholder="Phone No" v-model="phone">
                            <span v-if="(!$v.phone.required || $v.phone.$dirty)" class="text-danger">Phone number is required</span>
                            <span v-if="(!$v.phone.minLength || !$v.phone.maxLength)" class="text-danger">Phone number length should be 10</span>
                        </div>
                    </div>
                    <div class="row mb-3">
                        <label for="inputEmailAddress2" class="col-sm-3 col-form-label">Email Address</label>
                        <div class="col-sm-9">
                            <input type="email" class="form-control" id="inputEmailAddress2" placeholder="Email Address" v-model="email">
                            <span v-if="(!$v.email.required || $v.name.$dirty)" class="text-danger">Email is required</span>
                            <span v-if="!$v.email.email || $v.email.$dirty" class="text-danger">Valid Email is required</span>
                        </div>
                    </div>
                    <div class="row mb-3">
                        <label for="inputChoosePassword2" class="col-sm-3 col-form-label">Choose Password</label>
                        <div class="col-sm-9">
                            <input type="password" class="form-control" id="inputChoosePassword2" placeholder="Choose Password" v-model="password">
                            <span v-if="(!$v.password.required || $v.password.$dirty)" class="text-danger">Password is required</span>
                            <span v-if="(!$v.password.minLength || $v.password.$maxLength)" class="text-danger">Password length must be between {{ $v.password.$params.minLength.min }} and {{ $v.password.$params.maxLength.max}} </span>

                        </div>
                    </div>
                    <div class="row mb-3">
                        <label for="inputAddress4" class="col-sm-3 col-form-label">Address</label>
                        <div class="col-sm-9">
                            <textarea class="form-control" id="inputAddress4" rows="3" placeholder="Address" v-model="address"></textarea>
                            <span v-if="!$v.address.required" class="text-danger">Address is required</span>
                        </div>
                    </div>
                    <div class="row mb-3">
                        <label for="inputAddress4" class="col-sm-3 col-form-label"></label>
                        <div class="col-sm-9">
                            <div class="form-check">
                                <input class="form-check-input" type="checkbox" id="gridCheck4" v-model="check">
                                <label class="form-check-label" for="gridCheck4">Check me out</label>
                                <span v-if="!$v.check.required" class="text-danger">Accept Terms is required</span>
                            </div>
                        </div>
                    </div>
                    <div class="row">
                        <label class="col-sm-3 col-form-label"></label>
                        <div class="col-sm-9">
                            <input type="submit" class="btn btn-info px-5" value="Register"/>
                        </div>
                    </div>
                    </form>
                </div>
        
            </div>
        </div>
    </div>
</div>
</template>

<script>
import { required, minLength, maxLength, alpha, email } from 'vuelidate/lib/validators';
export default {

    name: 'Formvalid',
  
    data : ()=> ({
        name: '',
        email: '',
        phone: '',
        password: '',
        address: '',
        check: ''
        
    }),

    validations: {
        name : {
            required,
            alpha
        },
        email: {
            required,
            email
        },
        phone: {
            required,
            maxLength: maxLength(10),
            minLength: minLength(10)
        },
        password: {
            required,
            maxLength: maxLength(12),
            minLength: minLength(6)
        },
        address:{
            required
        },
        check: {
            required
        }
    },
    methods: {
        submitForm() {
            //this.$v.touch();

            if(!this.$v.$invalid){
                console.log("Name: "+(this.name)+", email: "+ (this.email)+" ,password: "+ this.password + (this.email) + " ,phone: "+ this.phone + ", Accept Terms: " +this.check)

            }
        }
    }
}
</script>
<style scoped>

</style>