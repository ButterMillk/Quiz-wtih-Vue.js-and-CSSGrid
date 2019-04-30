<template>
  <div id="app">
      <hr />
      <div class="navigation">
        <h1>Pseudo-Milionerzy</h1>
      </div>
      <hr />

      <div class="container">
        <Informations :gamer="gamer" />
        <Question :textQuestion="Questions[game].question" /> 
          <Answer :textAnswer="Questions[game].answers[0]" 
                  @selectAnswer="updateData($event)"/>
          <Answer :textAnswer="Questions[game].answers[1]" 
                  @selectAnswer="updateData($event)"/>
          <Answer :textAnswer="Questions[game].answers[2]" 
                  @selectAnswer="updateData($event)"/>
          <Answer :textAnswer="Questions[game].answers[3]" 
                  @selectAnswer="updateData($event)"/> 
      </div>
      <hr />
      <div class="control">
        <button>Następna runda</button>
        <button @click="this.endGame">Koniec gry</button>
      </div>
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
        {idQuestion: 3, question: "Która z poniższych osób nie była prezydentem Polski?", answers: [
          {idAnsewer: 1, answer: "Lech Kaczyński", truth: false},
          {idAnsewer: 2, answer: "Donald Tusk", truth: true},
          {idAnsewer: 3, answer: "Bronisław Komorowski", truth: false},
          {idAnsewer: 4, answer: "Lech Wałęsa", truth: false},
          ],
        },
        {idQuestion: 4, question: "Jaki jest najstarszy klub piłkarski w Polsce?", answers: [
          {idAnsewer: 1, answer: "Wisła Kraków", truth: false},
          {idAnsewer: 2, answer: "Legia Warszawa", truth: false},
          {idAnsewer: 3, answer: "Górnik Zabrze", truth: false},
          {idAnsewer: 4, answer: "Cracovia", truth: true},
          ],
        },
        {idQuestion: 5, question: "Wskaż datę zakończenia I wojny światowej...", answers: [
          {idAnsewer: 1, answer: "11 listopada 1918", truth: true},
          {idAnsewer: 2, answer: "10 listopada 1918", truth: false},
          {idAnsewer: 3, answer: "11 listopada 1917", truth: false},
          {idAnsewer: 4, answer: "11 listopada 1919", truth: false},
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
    // showText(){
    //   console.log("Tekst do propsowania: " + this.Questions[this.game].question);
    // },

    endGame(){
      
      this.gamer.score = 0;
      this.gamer.opportunities = 3;
      this.game = 0;
    },

    endGameDetails(){
      console.log("Twój wynik to: " + this.gamer.score + " punktów");
    },

    updateData(updatedObject){
      this.gamer.score += updatedObject.score;
      this.gamer.opportunities += updatedObject.opportunities;
      this.game++;
      if(this.game >= this.Questions.length){
        alert("Przepraszamy ale nie mamy więcej pytań - dodamy je wkrótce ;)");
        this.endGameDetails();
        this.endGame();
      }
    }
    
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
  margin: 0;
  padding: 0;
}

.control{
  text-align: center;
}


</style>
