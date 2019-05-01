<template>
    <transition
        @before-enter = "beforeEnter"
        @enter = "enter"
        @after-enter = "afterEnter"
        @enter-cancelled = "enterCancelled"

        @before-leave = "beforeLeave"
        @leave = "leave"
        @after-leave = "afterLeave"
        @leave-cancelled = "leaveCancelled"
        :css="false">
            <div class = "wrapperAnswer"  @click = "selectAnswer">
                <p>{{ textAnswer.answer }}</p>
            </div>
    </transition>
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
                this.selectedAnswer.score = 100;
                alert("Poprawna odpowiedź!");
            }
            else{
                this.selectedAnswer.opportunities = -1;
                alert("Błędna odpowiedź!");
            }

            this.$emit('selectAnswer', this.selectedAnswer);          
        },

        beforeEnter(element){
            console.log('beforeEnter');
            element.style.backgroundColor = "#FFFF99";
        },

        enter(element, done){
            console.log("To jest element z funkcji enter");
            element.style.backgroundColor = "red";
            done();
        },

        afterEnter(element){
            console.log("After enter");
        },

        enterCancelled(element){
            console.log("enter canceled");
        },

        beforeLeave(element){
            console.log("before Leave");
        },

        leave(element, done){
            console.log("enter canceled");
            done();
        },

        afterLeave(element){
            console.log("after leave");
        },
        
        leaveCancelled(element){
            console.log("leave cancelled");
        },

    },

}
</script>

<style scoped>
.wrapperAnswer{
    width: 100%;
    height: 100%;
    display: table;
}

.wrapperAnswer__true:active{
    animation: rotate-true 3s ease-out forwards;
}

.wrapperAnswer__false:active{
    animation: rotate-false 3s ease-out forwards;
}

p{
    display: table-cell;
    vertical-align: middle;  
}

/* .rotate-enter {
    
}

.rotate-enter-active {
    animation: rotate-in 1s ease-out forwards;
}

.rotate-leave {

}

.rotate-leave-active {
    animation: rotate-out 1s ease-out forwards;
    
} */

@keyframes rotate-true{
    from {
        transform: rotateY(0deg);

    }
    to {
        transform: rotateY(180deg);
        background-color: green;
    }
}

@keyframes rotate-false{
    from {
        transform: rotateY(0deg);

    }
    to {
        transform: rotateY(180deg);
        background-color: red;
    }
}


</style>