<template>
  <h1>{{ Header }}</h1>
  <button @click="start" :disabled="isPlaying" class="btn">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showScore" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Results from "./components/Results.vue";
export default {
  name: "App",
  components: { Block, Results },
  data() {
    return {
      Header: "THE BEST REACTION GAME TIMER",
      isPlaying: false,
      delay: null,
      score: null,
      showScore: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showScore = false;
      console.log(this.delay);
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showScore = true;
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
.btn {
  background-color: rgb(8, 43, 241);
  border-radius: 5px;
  outline: none;
  border-style: none;
  border-block-style: 0px;
  height: 50px;
  width: 150px;
  margin: 10px;
}
button[disabled] {
  opacity: -0.2;
  cursor: not-allowed;
}
</style>
