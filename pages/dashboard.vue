<template>
  <div class="bg-light-gray vh-100 pa3 tc">
    <h2 class="tc">Facebook authentication with Appwrite</h2>
    <div class="br3 bg-white ba dark-gray b--black-10 shadow-3 w-100 w-60-m w-30-l center mt5 ph4 pv4 mw6">
      <div class="f4 tl">
        <p class="navy fw7">Name:</p>
        <p>{{name}}</p>
        <p class="mt4 navy fw7">Email:</p>
        <p>{{email}}</p>
      </div>
      <button class="f6 link dim br3 pv2 ph3 mb2 dib white bg-navy ba b--navy pointer mt4 mt0-l inline-flex items-center" @click="logOutWithFacebook">
        Log out
        </button>
    </div>
  </div>
</template>
<script>
import {sdk} from '~/init';
  export default {
    data(){
      return{
        namme: '',
        email: '',
        response: ''
      }
    },
    mounted: function(){
        this.getUserSession()
    },
    methods: {
      getUserSession: async function(){
        try {
          this.response = await sdk.account.get()
          if (this.response) {
            this.name = this.response.name,
            this.email = this.response.email 
          }
          
        } catch (error) {
          console.log(error)
        }
      },
      logOutWithFacebook: async function(){
        try {
          await sdk.account.deleteSession('current')
          this.$router.push('/') 
        } catch (error) {
          console.log(error)
        }
      }
    }
  };

</script>