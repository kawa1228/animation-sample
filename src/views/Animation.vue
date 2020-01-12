<template>
  <div class="animation">
    <div class="content">
      <h1>Dolphin is cute</h1>
      <img src="../assets/image01.jpeg" alt="dolphin">
    </div>
    <div class="content">
      <h1>Stingray is beautiful</h1>
      <img src="../assets/image02.jpeg" alt="stingray">
    </div>
    <div class="content">
      <h1>Penguin looks cool</h1>
      <img src="../assets/image03.jpeg" alt="penguin">
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import {TweenMax} from "gsap";

export default {
  name: 'animation',
  components: {
    //
  },
  mounted() {
    //
  }
}
</script>
