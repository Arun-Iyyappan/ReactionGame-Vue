<template>
  <h1>Reaction Timer Game</h1>
  <button :disabled="isPlaying" @click="start">Play</button>
  <Block v-if="isPlaying" :delay="delay" @end="endgame" />
  <Output v-if="showResults" :score="score" />
</template>

<script>
import Block from "./components/Block.vue";
import Output from "./components/Output.vue";

export default {
  name: "App",
  components: { Block ,Output },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score : null,
      showResults:false
    };
  },
  methods: {
    start() {
      (this.delay = 2000 + Math.random() * 3000),
        (this.isPlaying = true),
       
        this.showResults=false
    },
    endgame(reactionTime){
         this.score  = reactionTime;
         this.isPlaying=false;
         this.showResults = true;
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top : 200px
}

button{
  background-color: aqua;
  color: black;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}

button[disabled]{
  opacity: 0.2;
  cursor: not-allowed;
}
</style>
