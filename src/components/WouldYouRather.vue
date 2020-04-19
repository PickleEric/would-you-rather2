<template>

<body>
    <div class='questionContainer'>
        <!--Display the question and radio buttons and link them with v-model -->
                <h2>{{ question.question }}</h2>

                <input type='radio' v-bind:id="question.answer1" v-model='choice' v-bind:value="question.answer1" v-on:change="checked(choice)">
                <label v-bind:for="question.answer1">{{ question.answer1 }}</label>
                <input type='radio' v-bind:id="question.answer1" v-model='choice' v-bind:value="question.answer2" v-on:change="checked(choice)">
                <label v-bind:for="question.answer2">{{ question.answer2 }}</label>

    </div>
</body>
</template>

<script>
export default {
    name: 'WouldYouRather',
    data() {
        return {
            choice: ''
        }
    },
    props: {
                question: Object, // this will take on functions from the parent 
            },
    methods: {
        checked(choice) {
                    let answer = { id: this.question.id, choice: this.choice}
                    this.$emit('answer-change', answer)// emits to the parent is a choice was changed
                }
    }
}
</script>

<style scoped>
.questionContainer {
    font-style: italic;
    background-image: linear-gradient(to right, aqua, orange);
    background-blend-mode: luminosity;
}


</style>