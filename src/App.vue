<template>
  <h1>Reflex Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <results :result="score" v-if="score"></results>
  <block v-if="isPlaying" :delay="delay" @end="endGame"></block>
</template>

<script>
import Block from './components/Block.vue';
import Results from './components/Results.vue';

export default {
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null
    };
  },
  methods: {
    start() {
      // get random number btw 2000 (2s) and 7000 (7s)
      this.delay = 2000 + Math.floor(Math.random() * 5000);
      this.isPlaying = true;
      this.score = null;
      console.log('clicking');
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
    }
  }
};
</script>

<style>
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  text-align: center;
  margin-top: 60px;
  color: #444;
}

button {
  background: #0faf87;
  color: #fff;
  padding: 8px 16px;
  font-size: 1rem;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
  border-radius: 4px;
  border: none;
}

button[disabled] {
  pointer-events: none;
  opacity: 0.2;
}
</style>
