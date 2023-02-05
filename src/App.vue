<template>
  <div class="flex flex-col justify-center items-center min-h-screen ">
    <Questions v-if="questionsAnswered<questions.length" :questions="questions" :questionsAnswered="questionsAnswered" @question-answered="questionAnswered"/>
    <Result v-else :totalCorrect="totalCorrect" :results="results"/>
    <button v-show="questionsAnswered == questions.length" @click.prevent="resetQuestions"  class="bg-cyan-500 py-2 px-6 rounded-2xl text-white hover:bg-cyan-600 my-2">Reset</button>
  </div>
</template>

<script >

import Questions from './components/Questions.vue';
  import Result from './components/Result.vue';
  export default{
    name:'app',
    components:{
      Questions, Result
    },
    data(){
      return{
        questionsAnswered:0,
        totalCorrect:0,
        questions:[
            {
              q:'What is 2+2?',
              answers:[
                {text:'4', is_correct:true},
                {text:'3', is_correct:false},
                {text:'8', is_correct:false},
                {text:'1', is_correct:false}
              ]
            },
            {
              q:'What is the capital of Iran?',
              answers:[
                {text:'Mashahad', is_correct:false},
                {text:'Tehran', is_correct:true},
                {text:'Tabriz', is_correct:false},
                {text:'New York', is_correct:false}
              ]
            },
            {
              q:'How many letters in "Beautiful?',
              answers:[
                {text:'8', is_correct:false},
                {text:'11', is_correct:false},
                {text:'10', is_correct:false},
                {text:'9', is_correct:true}
              ]
            },
        ],
        results:[
          {
            min:0,
            max:2,
            title:"try again",
            desc:"Do a little more and you'll succeed"
          },
          {
            min:3,
            max:3,
            title:"Wow, You're a genius!",
            desc:"all those nights of studying has paid off, huh?"
          }
        ]
      }
    },
    methods:{
      questionAnswered(is_correct){
        if(is_correct){
          this.totalCorrect++;
        }
        this.questionsAnswered++;
      },
      resetQuestions() {
        this.questionsAnswered = 0;
        this.totalCorrect = 0;
      }
    },
    computed:{
      
    }
  }
</script>

<style scoped>

</style>