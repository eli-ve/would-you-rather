<template>
  <div id="app">

    <h1>Would you rather...?</h1>

    <!--
    no html elements have dashes, so anything with a dash has
    to be a vue component - helps avoid confusion

    vvv references 'WouldYouRather' component vvv
     -->
    <would-you-rather v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"
    ></would-you-rather>

    <h2>{{ userSelectionMsg }}</h2>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {  // needs to be sent to WouldYouRather component
      wyrQuestion: 'Would you rather live in a cave or a tree house?',
      wyrAnswer1: 'cave',
      wyrAnswer2: 'tree house',
      userSelectionMsg: ''
    }
  },
  methods: {
    answerChanged(choice) {
      // NOTE: this is a template literal (uses backticks, NOT QUOTES)
      this.userSelectionMsg = `You chose ${choice}!`
    }
  }
}
</script>

<style>
body {
  background: darkslateblue;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: darkslateblue;
  background: lightskyblue;
  border: 4px darkslateblue dotted;
}
</style>
