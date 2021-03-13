<template>
  <div class="screen">
    <p>* Click as fast as possible when the green screen appears</p>
    <div class="screen--green" v-if="showScreen" @click.once="endTimer"></div>
  </div>
</template>

<script>
export default {
  props: ['timeout'],
  data() {
    return {
      responseTime: null,
      startTime: null,
      endTime: null,
      showScreen: false,
    };
  },
  mounted() {
    setTimeout(() => {
      this.showScreen = true;
      this.startTimer();
    }, this.timeout);
  },
  methods: {
    startTimer() {
      let d = new Date();
      this.startTime = d.getTime();
    },
    endTimer() {
      let d = new Date();
      this.endTime = d.getTime();
      this.responseTime = this.endTime - this.startTime;
      this.$emit('end', this.responseTime);
    },
  },
};
</script>

<style scoped>
.screen--green {
  height: 300px;
  width: 100%;
  background-color: #42b983;
}

p {
  font-weight: bold;
}
</style>
