<template>
  <div id="app">
      <hr />
      <div class="navigation">
        <h1>Milionerzy</h1>
      </div>
      <hr />

      <div class="container">
        <Informations :gamer="gamer" />
        <Question :textQuestion="Questions[game].question" /> 
        
    
          <Answer :textAnswer="Questions[game].answers[0]" />
          <Answer :textAnswer="Questions[game].answers[1]" />
          <Answer :textAnswer="Questions[game].answers[2]" />
          <Answer :textAnswer="Questions[game].answers[3]" /> 
       
        
      </div>

      <button @click="this.showText">Następna runda</button>
      <button @click="this.endGame">Koniec gry</button>
  </div>
</template>

<script>

import Question from './components/Question.vue';
import Informations from './components/Informations.vue';
import Answer from './components/Answer.vue';

export default {
  name: 'App',

  data() {
    return{
      
      game: 0,

      gamer: {
        score: 0,
        opportunities: 3,
      },

      Questions: [
        {idQuestion: 1, question: "Kto jest mistrzem Polski w hokeju na lodzie?", answers: [
          {idAnsewer: 1, answer: "Comarch Cracovia", truth: false},
          {idAnsewer: 2, answer: "GKS Tychy", truth: true},
          {idAnsewer: 3, answer: "TatrySki Podhale Nowy Targ", truth: false},
          {idAnsewer: 4, answer: "Tauron KH GKS Katowice", truth: false},
          ],
        },
        {idQuestion: 2, question: "Które miasto jest stolicą Niemiec?", answers: [
          {idAnsewer: 1, answer: "Hamburg", truth: false},
          {idAnsewer: 2, answer: "Frankfurt", truth: false},
          {idAnsewer: 3, answer: "Stuttgart", truth: false},
          {idAnsewer: 4, answer: "Berlin", truth: true},
          ],
        },
        

      ],
    };
  },

  components: {
    Question,
    Informations,
    Answer,
  },

  methods:{
    showText(){
      console.log("Tekst do propsowania: " + this.Questions[this.game].question);
    },

    endGame(){
      alert("Koniec gry!");
      this.gamer.score = 0;
      this.gamer.opportunities = 3;
    },
  },
}
</script>

<style>


#app{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

.navigation{
  text-align: center;
}
.container{
  box-sizing: border-box;
  
}


</style>
