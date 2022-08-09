<template>
    <div >
        <h1>Signup Form</h1>
        <form @submit.prevent="handleSubmit">
            <label>Email:</label>
            <input
                type="email"
                required
                :value="email"
                @input="$emit('update:email', $event.target.value)"
            >

            <label>Password:</label>
            <input
                type="password"
                required
                :value="password"
                @input="$emit('update:password', $event.target.value)"
            >
            <div v-if="passwordError" class="error">{{ passwordError }}</div>

            <label>Role:</label>
            <select :value="role" @input="$emit('update:role', $event.target.value)">
                <option value="Developer">Web Developer</option>
                <option value="Designer">Web Designer</option>
            </select>
            
            <label>Skills</label>
            <input
                type="text"
                :value="tempSkill"
                @keyup.middle="addSkill"
                @input="$emit('update:tempSkill', $event.target.value)"
            > 
            <div v-for="skill in skills" :key="skill" class="pill">
            <span @click="deleteSkill(skill)">{{ skill }}</span>
            </div>

            <div class="terms">
                <input
                    type="checkbox"
                    :value="terms"
                    @input="handleCheckbox"
                >
                <label>Accept terms and conditions</label>
            </div>

            <div class="submit">
                <button>Create an account</button>
            </div>
        </form>
    </div>
</template>

<script>
import { ref } from 'vue';

    export default {
        props: ['email', 'password', 'role', 'terms', 'skills', 'tempSkill'],
        emits: [
            'update:email', 
            'update:password', 
            'update:role', 
            'update:terms',
            'update:skills',
            'update:tempSkill',
            'click:submit',
        ],
        setup(props, { emit }) {
            const passwordError = ref(null);

            const deleteSkill = (skill) => {
                const newSkills = props.skills.filter((item) => {
                    return skill !== item
                });

                emit('update:skills', newSkills)
            }

            const addSkill = (e) => {
                if (e.key === ',' && props.tempSkill) {
                    if (!props.skills.includes(props.tempSkill)) {
                        const newSkills = [...props.skills, props.tempSkill];
                        emit('update:skills', newSkills);
                    }
                    emit('update:tempSkill', '');
                }
            };

            const handleCheckbox = () =>{
                emit('update:terms', !props.terms)
            }

            const handleSubmit = () => {
                passwordError.value = props.password.length > 5 ? 
                    '' : 'Password must be at least 6 chars long'

                if(!passwordError.value) {
                    emit('click:submit');
                }
            }

            return {
                deleteSkill,
                addSkill,
                handleCheckbox,
                passwordError,
                handleSubmit,
            }
        }
    }
</script>