<template>
  <div :class="{ isPlaying: isPlaying, firstLoad: firstLoad }">
    Reaction Time: {{ reactionTime }}ms
    <div class="description">{{ description }}</div>
  </div>
  <div v-if="errorClick" class="error-message">
    Please wait for 'stop time' prompt next time.
  </div>
</template>

<script>
export default {
  name: 'ReactionTime',
  props: {
    reactionTime: Number,
    isPlaying: Boolean,
    firstLoad: Boolean,
    errorClick: Boolean,
  },
  computed: {
    description() {
      switch (true) {
        case this.reactionTime < 0:
          return 'Wow! Faster than light itself!';
        case this.reactionTime < 250:
          return 'Astonishing!';
        case this.reactionTime < 300:
          return 'Very Good!';
        case this.reactionTime < 600:
          return 'Good Enough!';
        case this.reactionTime < 700:
          return 'Astonishingly Slow!';
        default:
          return 'Wow! Slower than a snail!';
      }
    },
  },
};
</script>

<style scoped>
.isPlaying {
  display: none;
}
.firstLoad {
  display: none;
}
.error-message {
  margin-top: 10px;
  color: rgb(255, 122, 122);
}
.description {
  margin-top: 5px;
  font-size: 1.5rem;
  color: green;
}
</style>
