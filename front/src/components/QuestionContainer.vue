<template>
  <div class="question-container">
    <el-container class="max-width" justify="center" align="center">
      <el-main>
          <el-row>
            <el-col justify="middle" :span="20">
              <div>
                {{question}}
              </div>
            </el-col>
            <el-col justify="middle" :span="4">
              <el-button  @click="questionHidden = !questionHidden" v-if="questionHidden" plain type="primary" icon="el-icon-arrow-down"></el-button>
              <el-button @click="questionHidden = !questionHidden" v-else plain type="primary" icon="el-icon-arrow-up"></el-button>
            </el-col>
          </el-row>
          <el-row class="min-height">
            <el-col justify="middle" align="middle" :span="24">
              <transition name="el-fade-in-linear">
              <div v-show="!questionHidden" >
                <p>{{answer}}</p>
                </div>
            </transition>
            </el-col>
          </el-row>
      </el-main>
      <el-footer class="p-0">
        <el-row>
          <el-button plain disabled type="primary"> 
            Poprzednie <span class="hide-on-mobile"> pytanie </span>
            </el-button>
          <el-button plain type="primary">
            Następne <span class="hide-on-mobile"> pytanie </span>
          </el-button>
        </el-row>
      </el-footer>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'QuestionContainer',
  data() {
    return {
      question: 'Powiedz kotku co masz w środku',
      answer: 'jajco23123 321111111111111111111111 11111111111111111111111111111111111 111111111111111111111111111111111',
      questionHidden: true,
    }
  },
}
</script>


<style scoped lang="scss">
.min-height {
  min-height: 100px;
}
@media (max-width: 600px) {
  .hide-on-mobile{
    display: none;
  }
}

</style>
