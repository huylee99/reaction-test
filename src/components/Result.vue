<template>
  <div class="result">
    <h2>Your response time is {{ result }} ms</h2>
    <h3>{{ rank }}</h3>
  </div>
</template>

<script>
export default {
  data() {
    return {
      rank: null,
    };
  },
  props: ['result'],
  mounted() {
    if (this.result > 300) {
      this.rank = 'Slow hand';
    } else {
      this.rank = 'Fast hand';
    }
  },
};
</script>

<style scoped>
.result {
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translate(-50%, 100%);
  color: #42b983;
  z-index: 999;
  cursor:not-allowed;
}
</style>
