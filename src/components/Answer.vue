<template>
    <div class="component center-block">
      <div class="panel panel-default">
        <!--<div class="panel-heading">Answer component</div>-->
        <div class="panel-body">
            <h2 class="text-center"><strong>That's Correct!</strong></h2>
            <hr>
            <button class="btn btn-primary btn-lg center-block"
                    @click="nextQuestion">Next Question</button>
        </div>
      </div>
    </div>
</template>

<script>
    export default {
        name: "answer",
        methods: {
            nextQuestion() {
                this.$emit('changeComponentViewEvent', 'appQuestion');
            }
        }
    }
</script>

<style scoped>
  .panel-body {
      background-color: palegreen;
  }

  .panel-body h2 {
      font-size: 36px;
      color: green;
  }
</style>
