<template>
    <div>
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