<template>
  <h2>Reaction Timer</h2>
  <button @click="start" :disabled="isplayng">play</button>
  <Block v-if="isplayng" :delay="delay" @end="endGame"/>
  <Results v-if="showResult" :score="score"/>

</template>

<script>
import Block  from "./components/Block.vue";
import Results from './components/Results.vue';
export default {
  name: 'App',
  components: { Block, Results },
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
