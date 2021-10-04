<template>
  <button @click="handlerClick()" :class="{ isPlaying: isPlaying }">
    {{ playMessage }}
  </button>
</template>

<script>
export default {
  name: 'PlayButton',
  props: {
    isPlaying: Boolean,
    firstLoad: Boolean,
  },
  methods: {
    handlerClick() {
      this.$emit('play');
    },
  },
  computed: {
    playMessage() {
      if (this.firstLoad == true) {
        return 'Play';
      } else {
        return 'Play Again';
      }
    },
  },
};
</script>

<style scoped>
button {
  background: rgb(0, 206, 0);
  border: 0;
  font-size: 1.5rem;
  display: block;
  margin: 20px auto;
  padding: 10px 20px;
  cursor: pointer;
}

.isPlaying {
  display: none;
}
</style>
