<template>
  <div id="app" :class="background">
    <CakeAnimation :clickNumber="clickNumber" />
    <Message :clickNumber="clickNumber" @addClick="updateClickNumber($event)" />
  </div>
</template>

<script>
import CakeAnimation from './components/CakeAnimation.vue'
import Message from './components/Message.vue'

export default {
  name: 'app',
  components: {
    CakeAnimation,
    Message
  }, 
  data: function() {
    return {
      clickNumber: 0,
    }
  },
  methods: {
    updateClickNumber: function(updatedClickNumber) {
      this.clickNumber = updatedClickNumber;
    }
  },
  computed: {
    background () {
      if(this.clickNumber < 7) {
          return "background1"
      } else {
          return "background2"
      }
    }
  },
}
</script>

<style>
#app {
  font-family: 'Permanent Marker', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  height: 100vh;
  position: relative;
}

.background1::before {
  content: "";
  top: 0; 
  left: 0;
  width: 100%; 
  height: 100%;
  position: absolute;
  background-image: url('./assets/happy-birthday.gif');
  background-size: auto 100vh;
  background-position: center;
  filter: grayscale(100%);
}

.background2::before {
  content: "";
  top: 0; 
  left: 0;
  width: 100%; 
  height: 100%;
  position: absolute;
  background-image: url('./assets/melody.jpg');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: right;
  filter: grayscale(100%);
}
</style>
