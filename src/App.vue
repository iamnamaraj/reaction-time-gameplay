<template>
  <h2>Test your reaction timing</h2>
  <button @click="start" :disabled="isplayng">play</button>
  <Block v-if="isplayng" :delay="delay" @end="endGame"/>
  <p v-if="showResult">Reaction time: {{ score }}ms</p>

</template>

<script>
import Block  from "./components/Block.vue";
export default {
  name: 'App',
  components: { Block },
  data() {
    return {
      isplayng:false,
      delay: null,
      score:null,
      showResult:false
    }
  },
  methods :
  {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isplayng = true
      this.showResult = false
    },
    endGame(reactionTime){
      this.score = reactionTime;
      this.isplayng = false;
      this.showResult = true;
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
