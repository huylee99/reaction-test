<template>
  <div class="screen">
    <p>* Click as fast as possible when the green screen appears</p>
    <div class="screen--green" @click.once="clickHandler" v-if="screen"></div>
  </div>
</template>

<script>
export default {
  props: ['screen'],
  methods: {
    clickHandler() {
      this.$emit('stop');
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
