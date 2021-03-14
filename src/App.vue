<template>
  <div id="app">
    <h1 class="title--main">Reaction Timer</h1>
    <h2 class="title--sub">Click {{ button }} to test your reaction</h2>
    <button class="btn--start" :disabled="gameStart" @click="startTest">
      {{ button }}
    </button>
    <Screen v-if="gameStart" :timeout="time" @end="end" />
    <Result v-if="showResult" :result="result" />
  </div>
</template>

<script>
import Screen from './components/Screen';
import Result from './components/Result';

export default {
  data() {
    return {
      button: 'Start',
      gameStart: false,
      time: null,
      result: null,
      showResult: false,
    };
  },
  components: { Screen, Result },
  methods: {
    startTest() {
      this.button = 'Start';
      this.gameStart = true;
      this.showResult = false;
      this.time = (Math.floor(Math.random() * 2) + 1) * 1000;
    },
    end(responseTime) {
      this.button = 'Retry';
      this.result = responseTime;
      this.gameStart = false;
      this.showResult = true;
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
  position: relative;
}

.title--main {
  color: #42b983;
}

.btn--start {
  background-color: #42b983;
  outline: none;
  border: none;
  padding: 15px 30px;
  color: #fff;
  font-size: 20px;
  font-weight: bold;
  border-radius: 10px;
  cursor: pointer;
  transition: background-color 0.2s linear;
}

.btn--start:disabled {
  opacity: 0.5;
  cursor:not-allowed;
}
</style>
