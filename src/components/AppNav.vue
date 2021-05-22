<template>
    <div class=" w-full lg:w-8/12 xl:w-full xl:px-80 mx-auto flex justify-between bg-indigo-700 text-white">
        <ul class="flex items-center">
          <li>
              <router-link class=" text-sm inline-block p-3" to="/">Home</router-link>
          </li>
           <li>
             <router-link :to="{name: 'Upload'}" class=" text-sm inline-block p-3">Upload File</router-link>
          </li>
        </ul>
        <template v-if="!authenticated">
          <ul class="flex items-center">
            <li>
              <router-link class=" text-sm inline-block p-3" to="/login">Sign in</router-link>
            </li>
            <li>
              <router-link class=" text-sm inline-block p-3" to="/register">Create Account</router-link>
            </li>
          </ul>
        </template>
        <template v-if="authenticated">
          <ul class="flex items-center">
            <li>
              <router-link class=" text-sm inline-block p-3" to="/login">{{user.name}}</router-link>
            </li>
            <li>
              <a href="#" @click.prevent="logout" class=" text-sm inline-block p-3">Logout</a>
            </li>
          </ul>
        </template>
    </div>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  name: 'AppNav',
  computed:{
    ...mapGetters({
      authenticated: 'auth/authenticated',
      user: 'auth/user'
    })
  },
  methods:{
    ...mapActions({
      logoutAction: 'auth/logout'
    }),
    logout(){
      this.logoutAction()
      this.$router.replace({ name: 'Home'})
    }
  }
}
</script>
