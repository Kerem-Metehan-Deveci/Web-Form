<template>
    <v-form
        v-model:email="email"
        v-model:password="password"
        v-model:role="role"
        v-model:terms="terms"
        v-model:skills="skills"
        v-model:tempSkill="tempSkill"
        @click:submit="handleSubmit"
    />
    <v-results
        :email="email"
        :password="password"
        :role="role"
        :terms="terms"
    />
</template>

<script>
import VForm from './VForm.vue';
import VResults from './VResults.vue';

export default {
    components: {
        VForm,
        VResults,
    },
    data() {
        return{
            email: '',
            password: '' ,
            role: 'Designer',
            terms: false ,
            tempSkill: '',
            skills: [],
            passwordError: ''
        }
    },
    methods: {
        handleSubmit() {
            console.log('email:' , this.email)
            console.log('password:' , this.password)
            console.log('role:' , this.role)
            console.log('skills:' , this.skills)
            console.log('terms accepted:' , this.terms)
        }
    }
}
</script>

<style>
form {
    max-width: 420px;
    margin: 30px auto;
    background: white;
    text-align: left;
    padding: 40px;  
    border-radius: 10px;
}
label {
    color: #708090;
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input , select{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #dddd;
    color: #555;
}
input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 16px 0 0;
    position: relative;
    top: 2px;
}
.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eeee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #555;
    cursor: pointer;
}
button {
    background: #B22222;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: black;
    border-radius: 20px;
    color: white;
}
.submit {
    text-align: center;
}
.error {
    color: #B22222;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
}


</style>