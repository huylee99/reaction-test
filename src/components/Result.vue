<template>
  <div class="result" v-if="end">
    <h2>Your response time is {{ time }} ms</h2>
  </div>
</template>

<script>
export default {
  props: ['time', 'end'],
};
</script>

<style scoped>
.result {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, 50%);
  color: #fff;
  z-index: 999;
}
</style>
