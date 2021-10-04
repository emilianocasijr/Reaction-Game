<template>
  <h1>Reaction Game</h1>
  <p :class="{ firstLoad: !firstLoad }">Click on play to start!</p>
  <PlayButton
    @play="handlerPlay()"
    :isPlaying="isPlaying"
    :firstLoad="firstLoad"
  />
  <StopButton
    @stopTime="handlerStop()"
    @errorClick="handlerErrorClick()"
    :isPlaying="isPlaying"
    :isWaiting="isWaiting"
  />
  <ReactionTime
    :isPlaying="isPlaying"
    :reactionTime="reactionTime"
    :firstLoad="firstLoad"
    :errorClick="errorClick"
  />
</template>

<script>
import PlayButton from './PlayButton.vue';
import StopButton from './StopButton.vue';
import ReactionTime from './ReactionTime.vue';

export default {
  name: 'GamePage',
  data() {
    return {
      isPlaying: false,
      reactionTime: 0,
      startTime: 0,
      firstLoad: true,
      waitTime: 0,
      isWaiting: false,
      errorClick: false,
    };
  },
  components: { PlayButton, StopButton, ReactionTime },
  methods: {
    handlerPlay() {
      this.errorClick = false;
      this.firstLoad = false;
      this.isPlaying = true;
      this.waitTime = Math.floor(Math.random() * 5000);
      this.isWaiting = true;
      this.startTime = Date.now(); // for the error click
      setTimeout(() => {
        this.startTime = Date.now();
        this.isWaiting = false;
      }, this.waitTime);
    },
    handlerStop() {
      this.isPlaying = false;
      this.reactionTime = Math.floor(Date.now() - this.startTime);
    },
    handlerErrorClick() {
      this.errorClick = true;
      this.isPlaying = false;
      this.reactionTime = Math.floor(
        Date.now() - this.startTime - this.waitTime
      );
    },
  },
};
</script>

<style scoped>
.firstLoad {
  display: none;
}
</style>
