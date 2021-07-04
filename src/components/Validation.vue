<template>
    <div>
        <h2>Vuelidation</h2>
        <form @submit.prevent="submitForm">
            <div class="form-group">
                <label for="name">Name</label>
                <input type="text" v-model="name" class="form-control">
                <span class="text-danger" v-if="!$v.name.required || $v.name.dirty">Name is required</span>
                <span v-if="!$v.name.alpha" class="text-danger" >Name should contain alphabets</span>
            </div>

            <div class="form-group">
                <label for="name">Email</label>
                <input type="text" v-model='email' class="form-control">
                <span class="text-danger" v-if="!$v.email.required && $v.email.dirty">Name is required</span>
                <span v-if="!$v.email.email" class="text-danger" >Name should contain alphabets</span>
            </div>

            
            
        </form>
    </div>
</template>
<script>
import { required, minLength, maxLength, alpha, email } from 'vuelidate/lib/validators'

export default {

    name: 'Validation',
    
    data: ()=>({
        name: '',
        email: '',
        password: '',
        gender: '',
        acceptTerms: ''
    }),

    validations: {
        name: {
            required,
            alpha
        },
        email: {
            required,
            email
        },
        password: {
            required,
            maxLength: maxLength(12),
            minLength: minLength(6)
        },
        gender: {
            required
        },
        acceptTerms: {
            required
        }
    },
    methods: {
        submitForm(){
            this.$v.$touch()
            if(!this.$v.$invalid) {
                console.log(`Name: $(this.name), Email: $(this.email), Password: $(this.password), Gender: $(this.gender), AcceptTerms: $(this.acceptTerms)`)
            }
        }
    }
}
</script>
<style scoped>

</style>