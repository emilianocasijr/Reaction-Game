<template>
  <button
    v-if="isWaiting === false"
    :class="{ isPlaying: isPlaying }"
    @click="handlerClick()"
  >
    Stop time!
  </button>
  <button
    v-else
    class="waitButton"
    :class="{ isPlaying: isPlaying }"
    @click="handlerErrorClick()"
  >
    Get ready...
  </button>
</template>

<script>
export default {
  name: 'StopButton',
  props: {
    isPlaying: Boolean,
    isWaiting: Boolean,
  },
  methods: {
    handlerClick() {
      this.$emit('stopTime');
    },
    handlerErrorClick() {
      this.$emit('errorClick');
    },
  },
};
</script>

<style scoped>
button {
  background: rgb(0, 206, 0);
  border: 0;
  font-size: 2rem;
  padding: 20px 30px;
  cursor: pointer;
  display: none;
}

.isPlaying {
  display: block;
  margin: auto;
}

.waitButton {
  background-color: transparent;
  color: grey;
}
</style>
