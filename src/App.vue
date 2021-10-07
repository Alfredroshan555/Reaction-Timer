<template>
  <div class="container">
    <h1>Reaction Timer Game</h1>
    <button @click="start" :disabled="isPlaying">Play</button>
    <Block v-if="isPlaying" :delay="delay" @end="endGame" />
    <!-- <h4 v-if="showResults">Reaction Time : {{ score }}ms</h4> -->
    <Results v-if="showResults" :score="score"/>
  </div>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Result.vue'

  export default{
    name: 'App',
    components: { Block,Results },
    data() {
      return {
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false
      }
    },
    methods: {
      start(){
        this.delay = 2000 + Math.random() * 5000
        this.isPlaying = true
        console.log(this.delay)
      },
      endGame(reactionTime){
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
      }
    },
  }
  
  
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #d1d7dd;
  margin-top: 60px;
}
button{
  background: #0faf87;
  color: aliceblue;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  margin: 10px;
  cursor: pointer;
}
button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
body{
background: #000428;  /* fallback for old browsers */
background: -webkit-linear-gradient(to right, #004e92, #000428);  /* Chrome 10-25, Safari 5.1-6 */
background: linear-gradient(to right, #004e92, #000428); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

}
.container{
  border: 3px solid rgb(255, 255, 255);

  
  text-align: center;
  align-content: center;
}
</style>
