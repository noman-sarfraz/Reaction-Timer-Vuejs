<template>
  <div class="block" @click="stop">Click me as soon as you can</div>
</template>

<script>
export default {
  props: ["interval", "toggleIsPlaying", "toggleShowResult", "toggleDisablePlayButton"],
  methods: {
    stop() {
      clearInterval(parseInt(this.interval))
      this.toggleShowResult()
      this.toggleIsPlaying()
      this.toggleDisablePlayButton()
    }
  }
}
</script>

<style scoped>
.block {
  padding: 20px;
  background-color: teal;
  color: white;
  border-radius: 5px;
  margin: 10px;
  width: 30%;
  display: block;
  margin: auto;
  margin-top: 20px;
  padding-top: 50px;
  padding-bottom: 50px;
  
}
</style>
