<template>
  <div>
    <h1>Reaction Timer</h1>
    <button @click="start" :disabled="isPlaying">Start</button>
    <Block :delay="delay" v-if="isPlaying" @end="endGame" />
    <Results v-if="showScore" :score="score" />
  </div>
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";

export default {
  name: "App",
  data() {
    return {
      isPlaying: false,
      showScore: false,
      delay: null,
      score: null,
    };
  },

  methods: {
    start() {
      this.isPlaying = true;
      this.delay = 2000 + Math.random() * 1000;
      this.showScore = false;
    },

    endGame(reactionTime) {
      this.isPlaying = false;
      this.score = reactionTime;
      this.showScore = true;
    },
  },
  components: { Block, Results },
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
  cursor: pointer;
  margin: 10px;
}

button[disabled] {
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
