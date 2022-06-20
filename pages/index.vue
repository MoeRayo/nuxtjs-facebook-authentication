<template>
  <div class="bg-light-gray vh-100 pa3 tc">
    <h2>Facebook authentication with Appwrite</h2>
    <div class="br3 bg-white ba dark-gray b--black-10 shadow-3 w-100 w-60-m w-30-l mw6 center mt5 ph4 pv4">
      <p class="f4">Click on this button to login</p>
        <button class="f6 link dim br3 pv2 ph2 mb2 dib white bg-navy ba b--navy pointer mt3 mt0-l inline-flex items-center" @click="loginWithFacebook">
          <svg class="dib h2 w1" fill="currentColor" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill-rule="evenodd" clip-rule="evenodd" stroke-linejoin="round" stroke-miterlimit="1.414"><path d="M15.117 0H.883C.395 0 0 .395 0 .883v14.234c0 .488.395.883.883.883h7.663V9.804H6.46V7.39h2.086V5.607c0-2.066 1.262-3.19 3.106-3.19.883 0 1.642.064 1.863.094v2.16h-1.28c-1 0-1.195.476-1.195 1.176v1.54h2.39l-.31 2.416h-2.08V16h4.077c.488 0 .883-.395.883-.883V.883C16 .395 15.605 0 15.117 0" fill-rule="nonzero"/></svg>
          <span class="f6 ml2 pr2">Login with Facebook</span>
        </button>
    </div>
  </div>
</template>

<script>
import {sdk} from '~/init.js'
export default {
  methods: {

    loginWithFacebook: async function(){
      try {
        await sdk.account.createOAuth2Session('facebook', 'http://localhost:3000/dashboard')
      } catch (error) {
        console.log(error)
      }
    }
  }
}
</script>