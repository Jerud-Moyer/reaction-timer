<template>
  <h1>Test your reaction time!</h1>
  <button @click='start' :disabled='isPlaying'>play</button>
  <Block
    v-if='isPlaying'
    :delay='delay'
    @end='endGame'
    class='all'
    :class="this.position"
  />
  <Results :reactionTime="score" v-if='showResults'/>
</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
      position: 'four',
      positions: ['one', 'two', 'three', 'four', 'five']
    }
  },
  methods: {
    start() {
      this.position = this.positions[Math.floor(Math.random() * 5)]
      console.log(this.position)
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime) {
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
  color: #444;
  margin-top: 60px;
}
.all {
  position: absolute;
}
.one {
  left: 20%;
  top: 70%;
}
.two {
  left: 60%;
  top: 10%;
}
.three {
  left: 40%;
  top: 40%;
}
.four {
  left: 80%;
  top: 60%;
}
.five {
  left: 30%;
  top: 40%;
}
</style>
