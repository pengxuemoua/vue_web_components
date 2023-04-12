<template>
  <div id="app">

    <h1>Would you rather?</h1>

    <!-- use v-bind so parent and child can communicate, v-on will listen to event in chlid component
    then the parent will hand the event by calling the answerChanged method-->

    <would-you-rather v-bind:key="question.id" 
    v-for="question in questions"
    v-bind:id="question.id"
    v-bind:question='question.wyrQuestion'
    v-bind:answer1='question.wyrAnswer1'
    v-bind:answer2='question.wyrAnswer2'
    v-on:answer-changed="answerChanged"
    ></would-you-rather>

    <h3>You would rather: </h3>
    
    <!-- use ul to display the user's answers -->
    <ul v-for="message in userSelectionMessages" v-bind:key="message">
      <li>{{ message }}</li>
    </ul>


  </div>

</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather // name of child component
  },
  data() {
    return {
      questions: [ // and array of question objects
        {
          id: 0, // id will be used so each radio button and answer can be tracked
          wyrQuestion: 'be an incredibly fast swimmer or an incredibily fast runner?',
          wyrAnswer1:'Be a fast swimmer', 
          wyrAnswer2:'Be a fast runner'
        },
        {
          id: 1,
          wyrQuestion:'be a detective or a pilot?',
          wyrAnswer1:'Be a detective', 
          wyrAnswer2:'Be a pilot'
        },
        {
          id: 2,
          wyrQuestion:'play hide and seek or dodgeball',
          wyrAnswer1:'Play hide and seek', 
          wyrAnswer2:'Play dodgeball'
        }
      ],
      userSelectionMessages: [] // empty array to store users choice that is sent from child component
    
    }
  },
  methods: {
    answerChanged(choice, wyrComponentID){ // event handler, payload includes two arugments from chlid component
      this.userSelectionMessages[wyrComponentID] = choice //update each choice using index value
    }
  }
}
</script>

<style>

body{
  background: #E4DCCF;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: #E4DCCF;
}

ul {
  list-style-type: square;
  list-style-position: inside;
}
</style>
