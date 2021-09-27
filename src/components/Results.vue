<template>
  <h1>Yor reaction time was:</h1>
  <h1>{{ this.reactionTime / 1000 }} seconds</h1>
  <h1 v-if='rank'>you are a {{ rank }}</h1>
</template>

<script>
export default {
  props: ['reactionTime'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    console.log('score = ', this.reactionTime)
    if(this.reactionTime < 250) {
      this.rank = 'Click Wizard!'
    } else if (this.reactionTime < 400) {
      this.rank = 'Ranger'
    } else {
      this.rank = 'noooob'
    }
  },
}
</script>

<style>

</style>