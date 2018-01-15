<template>
  <div class="container">
    <h1 class="text-center"><strong>The Super Quiz</strong></h1>
    <hr>
    <component :is="selectedComponent" @changeComponentViewEvent="selectedComponent=$event"></component>
  </div>
</template>

<script>
  import Question from './components/Question.vue';
  import Answer from './components/Answer.vue';

export default {
  name: 'app',
  data () {
    return {
      selectedComponent: 'appQuestion'
    }
  },
  components: {
    appQuestion: Question,
    appAnswer: Answer
  }
}
</script>

<style>
  div.component1 {
    border: 1px solid black;
    padding: 30px;
  }

  div.component {
    width: 500px;
  }

  .panel-heading {
    font-size: 24px;
    font-weight: 600;
  }

  table tr td button {
    margin-left: 80px;
  }

  .borderless tbody tr td, .borderless tbody tr th {
    border-top: none;
  }

  .question-item {
    display: inline-block;
    padding-left: 100px;
    padding-top: 20px;
    height: 90px;
    width: 200px;
  }
</style>
