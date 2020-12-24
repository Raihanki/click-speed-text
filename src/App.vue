<template>
  <h1>Gaou Click Speed Test</h1>
  <button class="playButton" @click="startGame" :disabled="isPlaying">play</button>
  <Block v-if="isPlaying" @end="endGame"></Block>
  <Result :resultClick="resultClick" v-if="showResult"></Result>
</template>

<script>
import Block from './components/Block.vue';
import Result from './components/Result.vue';

export default {
  name: 'App',
  components: { Block, Result },
  data () {
    return {
      isPlaying: false,
      resultClick: null,
      showResult: false,
    }
  },
  methods: {
    startGame() {
      this.isPlaying = true;
      this.showResult = false;
    },
    endGame(counter) {
      this.resultClick = counter;
      this.isPlaying = false;
      this.showResult = true;
    }
  }
}
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

.playButton {
  padding: 10px 20px;
  color: white;
  border: none;
  background: #5bb75b;
  border-radius: 5px;
  font-size: large;
}

.playButton:hover {
  background: green;
}

.playButton:focus {
  outline-width: thin;
  outline-color: darkgreen;
}

.playButton[disabled] {
  opacity: 0.4;
  cursor: not-allowed;
}
</style>
