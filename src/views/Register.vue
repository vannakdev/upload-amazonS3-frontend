<template>
    <div>
        <form @submit.prevent="login">
            <button type="submit">Login</button>
        </form>
    </div>
</template>
<script>
export default {
    methods:{
        login(){
            console.log('Login');
        }
    }
}
</script>
