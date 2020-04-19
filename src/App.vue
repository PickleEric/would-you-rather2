<template>

    <div id="app">
        <h1>Would you rather...</h1>
        
        <WouldYouRather 
        v-for="question in questions"
        v-bind:key="question.id"
        v-bind:question="question"
        v-on:answer-change="answerChanged"
        ></WouldYouRather>
          <ul>
            <li
            v-for="choice in choices"
            v-bind:key="choice.id"
            >{{ choice }}
            </li>
          </ul>
    </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue' // import our vue

export default {
  name: 'App',
  components: {
    WouldYouRather
    
  },
// quesitons array that holds our objects
  data() {
    return {
      questions: [
        {
          id: 0,
          question: '...stay in and save the world or go out and fight crime?',
          answer1: 'stay in',
          answer2: 'go out'
        },
        {
          id: 1,
          question: '...eat five skittles or one air head?',
          answer1: 'five skittles',
          answer2: 'one air head',
        },
        {
          id: 2,
          question: '...run for president or learn a new skill?',
          answer1: 'run for president',
          answer2: 'learn a new skill',
        },
      ],
      choices: [],// user choice array
    }
    
  },
  methods: {
    answerChanged(choice) {
      let index = choice.id
      this.choices[index]
      this.$set(this.choices, index, choice.choice)
//how not to repalce?

//push choices and sort by id 

// or add to the index given by the id

      //this.choices.push(answer)// push a new user choice in to the array
      //this.choices.forEach(e =>{
        //if (e.id = choice.id) {

        //}
      //}) 
      //this.choices.sort(function(c1, c2){
        //return c1.id > c1.id ? 1 : -1
      //})
    }
  },


}

</script>

<style>
ul {
  width: 150px;
  height: 100px;
  border: 5px solid #050505;

}
</style>
