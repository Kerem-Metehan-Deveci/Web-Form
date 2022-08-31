<template>
    <div class="Result">
        <p>Email: {{ email }}</p>
        <p>Password: {{ password }}</p>
        <p>Role: {{ role }}</p>
        <p>Terms Accepted: {{ terms }}</p>
    </div>
</template>

<script>
    export default {
        name: '' ,
        props: [
            'email',
            'password',
            'role',
            'terms'
        ],
    };
</script>
<style scoped>
    .Result {
        border: dashed black 1px;
        text-align: center;
        text-decoration: none;
        width: 300px;
        position: relative;
        margin: auto;
    }
</style>