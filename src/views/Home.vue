<template>
  <div class="home">
    <img ref="vue-logo" alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import {TweenMax} from "gsap";

export default {
  name: 'home',
  components: {
    HelloWorld
  },
  mounted() {
    const logo = this.$refs['vue-logo']
    console.log('logo', logo)
    TweenMax.to(logo, 1, {opacity: 0});
  }
}
</script>
