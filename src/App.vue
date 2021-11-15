<template>
  <div class="header">
    <h1>{{ heading }}</h1>
  </div>
  <Result :currentScore="currentScore"/>
  <TextWhoWins :messageBooleanObj="messageBooleanObj"/>
  <Selection @currentResult="result" @message="winLoseMessage"/>
  <p>{{ paragraph }}</p>
</template>

<script>
import Result from './components/Result.vue'
import TextWhoWins from './components/TextWhoWins.vue'
import Selection from './components/Selection.vue'

export default {
  name: 'App',
  components: { Result, TextWhoWins, Selection },
  data() {
    return {
      heading: 'Rock Paper Scissors',
      currentScore: {},
      messageBooleanObj: {},
      paragraph: 'Make your move.'
    }
  },
  methods: {
    result(score) {
      this.currentScore = score
    },
    winLoseMessage(messageBoolean) {
      this.messageBooleanObj = messageBoolean
      console.log(this.messageBooleanObj)
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
}
.header {
  margin-top: -8px;
  margin-left: -8px;
}
.header h1 {
  background: white;
  width: 100%;
  text-align: center;
  margin: auto;
  font-weight: bold;
  padding: 20px;
}
p {
  color: white;
  font-weight: bold;
  margin: 20px auto;
}
</style>
