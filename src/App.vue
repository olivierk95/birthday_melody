<template>
  <div id="app" :style="backgroundImage">
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
    backgroundImage () {
      if(this.clickNumber < 7) {
          return {
            "--background": " url('./assets/happy-birthday.gif')"
          };
      } else {
          return {
            "--background": " url('./assets/melody.jpg')"
          };
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

#app::before {
  content: "";
  top: 0; left: 0;
  width: 100%; 
  height: 100%;
  position: absolute;
  background-image: var(--background);
  background-size: auto 100vh;
  background-position: center;
  filter: grayscale(100%);
}
</style>
