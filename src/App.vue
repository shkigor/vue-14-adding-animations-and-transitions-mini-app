<template>
  <div class="container">
    <h1 class="text-center"><strong>The Super Quiz</strong></h1>
    <hr>
    <transition name="flip" mode="out-in">
      <component :is="selectedComponent" @changeComponentViewEvent="selectedComponent=$event"></component>
    </transition>
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


  .flip-enter {
    /*transform: rotateY(0deg);*/
  }

  .flip-enter-active {
    animation: flip-in  0.5s ease-out forwards;
  }

  .flip-leave {
    /*transform: rotateY(0deg);*/
  }

  .flip-leave-active {
    animation: flip-out 0.5s ease-out forwards;
  }

  @keyframes flip-out {
    from {
      transform: rotateY(0deg);
    }
    to {
      transform: rotateY(90deg);
    }
  }

  @keyframes flip-in {
    from {
      transform: rotateY(90deg);
    }
    to {
      transform: rotateY(0deg);
    }
  }
</style>
