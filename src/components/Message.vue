<template id="message">
  <div>
    <h2 v-show="display" :style="{color: textColor}"> {{ comment }}</h2>
    <button v-show="replay" @click="handleClick"> {{ button }} </button>
    <button v-show="!replay" @click="replayExperience"> Replay </button>
    <h1> Happy Birthday Melody! </h1>
    <h3> *Have mercy on me for the delay </h3>
  </div>
</template>

<script>

export default {
  name: 'Message',
  props: {
    clickNumber: {
      type: Number
    }
  },
  data: function() {
    return {
      button: "Blow on the screen",
      display: false, 
      comment: "Did you really try to blow on the screen? I can't believe I missed this! There is one candle left your loser...",
      textColor: "black",
      replay: true
    }
  },
  methods: {
    handleClick: function() {
      this.$emit("addClick", this.clickNumber+=1);
      if (this.clickNumber == 1) {
        this.button = "Blow again",
        this.display = true,
        this.comment = "Did you really try to blow on the screen? I can't believe I missed this! There is one candle left your loser..."
      } else if (this.clickNumber == 2) {
        this.button = "Eat it",
        this.comment = "Well done! Now you can eat the cake now."
      } else if (this.clickNumber == 3) {
        this.button = "Eat more",
        this.comment = "Your level of fat is not high enough..."
      } else if (this.clickNumber == 4) {
        this.button = "EAT THAT ONE LEFT",
        this.comment = "You are damn too slim!"
      } else if (this.clickNumber == 5) {
        this.button = "You rule",
        this.comment = "You did it! Don't look at your belly, it's about to explode."
      } else if (this.clickNumber == 6) {
        this.button = "It's done",
        this.comment = "Don't try to fool me, I can't offer you more... You have eaten way too much"
      } else if (this.clickNumber == 7) {
        this.replay = false,
        this.comment = "Ok, a last shitty message... I wish you the best of the best for you trip in Australia! I miss you darling <3",
        this.textColor = "white"
      } 
    },
    replayExperience: function () {
      this.$emit("addClick", this.clickNumber = 0);
      this.replay = true;
      this.button = "Blow on the screen";
      this.comment = "";
      this.textColor = "black"
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
    position: relative;
}

h1 {
    font-size: 3rem;
    color: #e52b49;
    animation: colorChange 2s 0s infinite alternate forwards;
}

@keyframes colorChange {
    0% {color: #e52b49}
    25% {color: #ff9811}
    50% {color: #ffcd00}
    75% {color: #ff6243}
    100% {color: #ff3051}
}

h3 {
    font-size: 1rem;
    position: fixed;
    bottom: 1rem;
    right: 1rem;
    background-color: rgba(255, 255, 255, 0.5);
    padding: .2rem;
}

button {
    cursor: pointer;
    font-family:  'Permanent Marker', cursive;
    color: white;
    background-color: rgb(226, 43, 43);
    text-decoration: none;
    border-radius: .4rem;
    border: none;
    padding: .3rem;
    font-size: .8rem;
    margin: 1rem;
}

</style>