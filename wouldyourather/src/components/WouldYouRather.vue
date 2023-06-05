<template>
  <div class="wyr">

    <h2>Please make your choice!</h2>

    <h3>{{ question }}</h3>

    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade">
    <label>{{ answer1 }}</label>

    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  // data sent from parent > child is called 'props' - used locally, it's just 'data'
  props: {
    question: String,
    answer1: String,
    answer2: String
  },
  data() {
    return {
      choice: ''
    }
  },
  methods: {
    // can use console.log to check if method is being called
    choiceMade() {
      // can use *any* non-reserved word(s) as event name
      this.$emit('answer-changed', this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

.wyr {
  margin-bottom: 2rem;
}

</style>
