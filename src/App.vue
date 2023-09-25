<template>
  <h1>Reaction Time Game</h1>
  <button class="start-button" :disabled="isStart" @click="handleStart">
    Play
  </button>

  <Block v-if="isStart" :delay="delay" @end="endGame" />
  <Results v-if="score !== null" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  data() {
    return {
      isStart: false,
      delay: null,
      score: null,
    };
  },
  components: {
    Block,
    Results,
  },
  methods: {
    handleStart() {
      this.delay = 2000 + Math.random() * 5000;
      this.isStart = true;
      this.score = null;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isStart = false;
    },
  },
};
</script>

<style>
.start-button {
  padding: 12px 24px;
  font-size: 16px;
  outline: none;
  border: none;
  width: 10vw;
  border-radius: 4px;
  background: lightgreen;
  cursor: pointer;
}

button[disabled] {
  cursor: not-allowed;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  margin: 0;
}
</style>
