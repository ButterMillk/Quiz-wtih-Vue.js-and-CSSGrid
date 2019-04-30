<template>
    <div class="wrapperAnswer" @click="selectAnswer">
        <p>{{ textAnswer.answer }}</p>
    </div>
</template>

<script>
export default {
    name: 'Answer',
    data() {
        return{
            selectedAnswer: {
                score: 0,
                opportunities: 0,
            },
        }
    },
    props:{
        textAnswer: Object,
    },
    methods:{
        selectAnswer(){
            this.selectedAnswer.score = 0;
            this.selectedAnswer.opportunities = 0;
            if(this.textAnswer.truth){
                alert("Dobra odpowiedź");
                this.selectedAnswer.score = 100;
                console.log("Ile punktów?: "+this.selectedAnswer.score);
            }
            else{
                alert("Zła odpowiedź. -1 szansa");
                this.selectedAnswer.opportunities = -1;
                console.log("Ile minusów: "+this.selectedAnswer.opportunities);
            }
            
            console.log("Obiekt do zwrotu: " + this.selectedAnswer.score + " " + this.selectedAnswer.opportunities);
            this.$emit('selectAnswer', this.selectedAnswer);
                    
        }
    },

}
</script>

<style scoped>
.wrapperAnswer{
    box-sizing: border-box;
    width: 25vw;
    background-color: #FFFF99;
    text-align: center;
    display: inline-block;
    padding: 2px 3px;
    margin-left: -3px;
    cursor: pointer;
}

</style>