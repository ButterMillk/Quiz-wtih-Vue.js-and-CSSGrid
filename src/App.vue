<template>
  <div id="app">
    <p :text="this.textInput">Siema {{textInput}}</p>
      <Question />
  </div>
</template>

<script>

import Question from './components/Question.vue';
export default {
  name: 'App',

  data() {
    return{
      textInput: '',
    };
  },

  components: {
    Question,
  },


}
</script>

<style>
#app{
  box-sizing: border-box;

}

</style>
