<template>
  <div class="question-container">
    <el-container class="max-width" justify="center" align="center">
      <el-main>
          <el-row>
            <el-col justify="center" :span="20">
              <div id="question">
                {{currentQuestion.questionText}}
              </div>
            </el-col>
            <el-col justify="center" :span="4">
              <el-button @click="questionHidden = !questionHidden" v-if="questionHidden" plain type="primary" icon="el-icon-arrow-down"></el-button>
              <el-button @click="questionHidden = !questionHidden" v-else plain type="primary" icon="el-icon-arrow-up"></el-button>
            </el-col>
          </el-row>
          <el-row class="min-height">
            <el-col :span="24">
              <transition name="el-fade-in-linear">
                <div v-show="!questionHidden" >
                  <p>{{currentQuestion.answer}}</p>
                </div>
              </transition>
            </el-col>
          </el-row>
      </el-main>
      <el-footer class="p-0">
        <el-row>
          <el-button plain type="primary" @click="previous" :disabled="questionsHistory.length===0">
            Previous <span class="hide-on-mobile"> question </span>
          </el-button>
          <el-button plain type="primary" @click="next">
            Next <span class="hide-on-mobile"> question </span>
          </el-button>
        </el-row>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
import questions from '../assets/questions.json';

export default {
  name: 'QuestionContainer',
  data() {
    return {
      currentQuestionId: 0,
      questions,
      questionHidden: true,
      questionsHistory: [],
      disabled: false,
    }
  },
  mounted() {
    this.currentQuestionId = this.generateRandomQuestionId();
  },
  computed: {
    currentQuestion() {
      return this.questions[this.currentQuestionId];
    },
    maxQuestionId(){
      return this.questions.length;
    }
  },
  methods: {
    next() {
      this.questionHidden = true;
      this.questionsHistory.push(this.currentQuestionId);
      this.currentQuestionId = this.generateRandomQuestionId();
    },
    previous() {
      if (this.questionsHistory.length > 0) {
        this.currentQuestionId = this.questionsHistory.pop();
      }
    },
    generateRandomQuestionId() {
      return Math.floor(((Math.random()*this.maxQuestionId)) + 1)
    }
  }
}
</script>


<style scoped lang="scss">
.min-height {
  min-height: 100px;
}
#question {
  min-height: 40px;
  justify-content: center;
  align-items: center;
  display: flex;
  padding-right: 10px;
}
@media (max-width: 600px) {
  .hide-on-mobile{
    display: none;
  }
}
.el-fade-in-linear-leave-active {
  display: none !important;
}

</style>
