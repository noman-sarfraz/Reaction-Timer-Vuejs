<template>
  <h1 class="reaction-timer">Reaction Timer</h1>
  <button class="play-button" :class="{'disabled-play-button': disablePlayButton}" :disabled="disablePlayButton" @click="play">Play</button>
  <Block v-if="isPlaying" :interval="interval" :toggleIsPlaying="toggleIsPlaying" :toggleShowResult="toggleShowResult" :toggleDisablePlayButton="toggleDisablePlayButton" />
  <Result v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Result from "./components/Result.vue";

export default {

  components: { Block, Result },
  data() {
    return {
      delay: null,
      isPlaying: null,
      showResult: null,
      disablePlayButton: null,
      score: 0,
      interval: null
    }
  },
  methods: {
    play() {
      this.delay = 1000 + Math.random() * 1000
      this.disablePlayButton = true
      this.showResult = false
      setTimeout(() => {
        this.score = 0
        this.isPlaying = true
        this.interval = setInterval(() => {
          this.score += 10
        }, 10)
      }, this.delay);
    },
    toggleIsPlaying() {
      this.isPlaying = !this.isPlaying
    },
    toggleShowResult() {
      this.showResult = !this.showResult
    },
    toggleDisablePlayButton() {
      this.disablePlayButton = !this.disablePlayButton
    },
    
    
  },
  

}
</script>

<style>
#app {
  font-family: Comic Sans MS;
  text-align: center;
  color: teal;
  margin-top: 60px;
}
.play-button {
  padding: 5px 20px 10px 20px;
  font-size: 18px;
  font-family: comic Sans MS;
  color: white;
  background-color: teal;
  border: none;
  border-radius: 5px;
}
.disabled-play-button {
  padding: 5px 20px 10px 20px;
  font-size: 18px;
  font-family: comic Sans MS;
  color: white;
  background-color: #baf5f3;
  border: none;
  border-radius: 5px;
}
.reaction-timer {
text-decoration: underline;
}
</style>
