<template>
    <div class="w-2/4">
        <div class="progress">
            <!-- progress bar -->
            <div class="w-full bg-slate-300 rounded-md h-6 ">
                <div class="bar bg-cyan-400 h-6 rounded-md" :style="{width:`${(questionsAnswered/questions.length)*100}%` }">
                </div>
            </div>
            <!-- status -->
            <div class="status">{{ questionsAnswered }} out of {{ questions.length }} questions answered.</div>
        </div>
        <div class="p-2 mx-auto bg-slate-500" v-for="(question,qi) in questions" :key="question.q" v-show="questionsAnswered===qi">
            <div class="bg-red-500 p-4 rounded-2xl text-center text-white">{{ question.q }}</div>
            <div class="" >
                <div class="bg-orange-400 hover:bg-lime-500 cursor-pointer my-1 p-4 rounded-2xl text-center text-white" v-for="answer in question.answers" @click.prevent="selectAnswer(answer.is_correct)"><p class="font-sans font-medium">{{ answer.text }}</p></div>
            </div>
        </div>
    </div>
</template>

<script >
    export default {
    props: ["questions","questionsAnswered"],
    emits:['question-answered'],
    methods:{
        selectAnswer(is_correct){
            this.$emit('question-answered',is_correct)
        }
    }
    }
</script>

<style  scoped>
.bar{
    width: 0%;
}
</style>