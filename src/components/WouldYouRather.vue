<template>
  <div class="wyr">
    
    <h2>Would you rather...</h2>
    
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
  props: { // recieves data from parent
    id: Number,
    question: String,
    answer1: String,
    answer2: String,
  },
  data() {
    return{
      choice: '' // choice will be emitted to parent to inform the user's wyr answer
    }
  },
  methods: {
    choiceMade() {
      this.$emit('answer-changed', this.choice, this.id) // method name is answer-changed, payload of choice and id
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
  border: 2px #F4EEE0 solid;
  background: #F9E2AF;
  margin: 10px;
}

</style>
