<template>
  <div id="app">
    <el-container class="max-width">
      <el-main class="p-0">
        <el-tabs type="border-card" v-model="activeName">
          <el-tab-pane label="Category 1" name="first"><QuestionContainer /> </el-tab-pane>
          <el-tab-pane disabled label="Category 2" name="second">Kategoria 2</el-tab-pane>
        </el-tabs>
      </el-main>
    </el-container>
  </div>
</template>

<script>
import QuestionContainer from './components/QuestionContainer';

export default {
  name: 'App',
  data() {
    return {
      activeName: 'first'
    };
  },
  components: {
    QuestionContainer,
  }
}
</script>

<style lang="scss">
#app {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  .max-width {
    max-width: 500px;
  }
}
@media (max-width: 600px) {
  .p-0 {
    padding: 0 !important;
  }
}
</style>
