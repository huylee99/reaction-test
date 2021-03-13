<template>
  <div id="app">
    <h1 class="title--main">Reaction Timer</h1>
    <h2 class="title--sub">Click Start to test your reaction</h2>
    <button class="btn--start" @click="startTimeout" :disabled="disabled">
      Start
    </button>
    <Screen @stop="endTimer" :screen="showScreen" />
    <Result :time="responseTime" :end="showResult" />
  </div>
</template>

<script>
import Screen from './components/Screen';
import Result from './components/Result';

export default {
  data() {
    return {
      disabled: false,
      showScreen: false,
      showResult: false,
      timeStart: 0,
      timeClick: 0,
      responseTime: 0,
    };
  },
  name: 'App',
  components: { Screen, Result },
  methods: {
    startTimer() {
      this.showScreen = !this.showScreen;
      let d = new Date();
      this.timeStart = d.getTime();
    },
    endTimer() {
      this.disabled = false;
      this.showResult = !this.showResult;
      let d = new Date();
      this.timeClick = d.getTime();
      this.responseTime = this.timeClick - this.timeStart;
    },
    startTimeout() {
      this.disabled = true;
      this.showScreen = false;
      this.showResult = false;
      let time = (Math.floor(Math.random() * 3) + 2) * 1000;
      setTimeout(this.startTimer, time);
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
}
</style>
