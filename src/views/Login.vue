<template>
    <div class="w-10/12 xl:w-3/12 lg:w-4/12 md:w-3/12 mx-auto my-32">
        <form @submit.prevent="login" class="bg-gray-100 p-10 rounded-3xl mb-3 text-left">
            <div class="mb-6">
                <div class="mb-3 text-left">
                    <label class=" inline-block text-sm mb-2" for="email">Email Address</label>
                    <input v-model="form.email" class="w-full border-2 border-gray-200 h-10 px-3 rounded-md" type="email" name="" id="">
                </div>
                <div class="mb-3 text-left">
                    <label class=" inline-block text-sm mb-2" for="password">Password</label>
                    <input v-model="form.password" class="w-full border-2 border-gray-200 h-10 px-3 rounded-md" type="password" name="" id="">
                </div>
            </div>
            <button class=" bg-indigo-500 text-white px-4 py-3 leading-none rounded-lg font-medium mb-2" type="submit">Login</button>
            <p>Not Join yet? <a href="" class=" text-indigo-700">Create an account</a></p>
        </form>
    </div>
</template>
<script>
import { mapActions } from 'vuex'
export default {
    data(){
        return {
            form : {
                email : '',
                password:''
            }
        }
    },
    methods:{
        ...mapActions({
            loginAction:'auth/login'
        }),
        async login(){
            await this.loginAction(this.form)
            this.$router.replace({'name' : 'Home'})
        }
    }
}
</script>
