<template>
  <div class="result-container">
    <h2>Reaction Time: {{ score }}ms</h2>
    <h2>Category: {{ category }}</h2>
  </div>

</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      category: null
    }
  },
  mounted() {
    if (parseInt(this.score) < 500) {
      this.category = "Very Fast"
    } else if (parseInt(this.score) < 1000) {
      this.category = "Fast"
    } else if (parseInt(this.score) < 1500) {
      this.category = "Normal"
    } else if (parseInt(this.score) < 2000) {
      this.category = "Slow"
    } else {
      this.category = "Too Slow"
    }
  }
}
</script>

<style scoped>
.result-container {
  border: 1px solid teal;
  display: block;
  margin: auto;
  width: 30%;
  margin-top: 10pt;
  font-weight: lighter;
}
</style>
