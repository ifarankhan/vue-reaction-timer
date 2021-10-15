<template>
  <img alt="Vue logo" src="./assets/game.jpg" />
  <h1>I want to play a game:</h1>
  <br />
  <button @click="playGame" :disabled="isPlaying">Lets Play</button>
  <Block v-if="isPlaying" :delay="delay" @score="endGame"></Block>

  <Results v-if="score" :score="score"></Results>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Result.vue";

export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: 0,
    };
  },
  methods: {
    playGame() {
      this.isPlaying = true;
      this.delay = 1000 + Math.random() * 5000;
      this.score = 0;
      // console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
    },
  },
  components: {
    //HelloWorld
    Block,
    Results,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
button {
  background: #0faf87;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
