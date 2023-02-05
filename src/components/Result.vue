<template>
    <div class="bg-slate-300 rounded-md flex flex-col justify-center items-center w-1/2 p-6">
        <!-- title -->
        <div class="p-2 font-sans font-bold">{{ results[getResultIndex].title }}</div>
        <!-- description -->
        <div class="font-sans font-medium">{{ results[getResultIndex].desc }}</div>
    </div>
</template>

<script >
    export default {
    props: ["totalCorrect","results"],
    computed:{
        getResultIndex(){
            let index=0;
            this.results.forEach((e,i)=>{
                if(e.min<=this.totalCorrect && e.max>=this.totalCorrect){
                    index=i;
                }
            });
            return index;
        }
    }
    }
    
</script>

<style scoped>

</style>