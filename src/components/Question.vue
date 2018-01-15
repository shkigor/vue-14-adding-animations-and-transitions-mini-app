<template>
    <div class="component center-block">
      <div class="panel panel-default">
        <div class="panel-heading text-center">What's {{ leftValue }} - {{ rightValue }}?</div>
        <div class="panel-body">
           <div
              class="question-item"
              v-for="btnAnswer in btnAnswers"
              >
                <button
                      class="btn btn-primary btn-lg"
                      @click="checkAnswer(btnAnswer, $event)"
                      >
                        {{ btnAnswer }}
                </button>
           </div>
        </div>
      </div>
    </div>
</template>

<script>
  function compareRandom(a, b) {
    return Math.random() - 0.5;
  }

    export default {
        name: "question",
        data() {
            return {
                leftValue: 1,
                rightValue: 1,
                maxValue: 100,
                btnAnswers: [23, -21, 45, 78]
            }
        },
        created() {
            this.startQueze();
          },
        computed: {
            computedAnswer() {
              return this.leftValue - this.rightValue;
            }
        },
        methods: {
            calculateRandomNumber(min, max) {
                // return Math.min(Math.floor(Math.random() * max) + 1, min);
                return Math.floor(Math.random() * max) + 1;
            },
            evaluateBtnAnswers() {
                let sign;
                (this.computedAnswer > 0) ? sign = 1 : sign = -1;

                for (let i = 0; i < this.btnAnswers.length - 1; i++) {
                  this.btnAnswers[i] = this.calculateRandomNumber(0, 100) * sign;
                }
                this.btnAnswers[3] = this.computedAnswer;
            },
            shuffleAnswers() {
                this.btnAnswers.sort(compareRandom);
            },
            startQueze() {
                // this.leftValue = Math.floor(Math.random() * this.maxValue);
                this.leftValue = this.calculateRandomNumber(0, 100);
                this.rightValue = this.calculateRandomNumber(0, 100);
                this.evaluateBtnAnswers();
                this.shuffleAnswers();
            },
            checkAnswer(userAnswer, event) {
                // console.log(userAnswer);
                // console.log(event.target.innerText);
                if (this.computedAnswer === userAnswer) {
                    this.$emit('changeComponentViewEvent', 'appAnswer');
                } else {
                    alert('Wrong, try again!');
                }
            }
        }
    }
</script>

<style scoped>

</style>
