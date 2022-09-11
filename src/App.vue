<template>
  <h1>MSO Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button>
  <div v-if="isPlaying">
    <Block :delay="delay" @end="endGame" />
  </div>
  <Result v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";
export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  components: {
    Block,
    Result,
    Result,
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.isPlaying = false;
      this.score = reactionTime;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  width: 200px;
  height: 40px;
  background-color: #0faf87;
  color: white;
  border: none;
  border-radius: 20px;
  cursor: pointer;
}
button:disabled {
  background-color: #0faf8747;
  cursor: not-allowed;
}
</style>
