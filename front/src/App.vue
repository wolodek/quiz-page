<template>
  <div id="app">
    <el-container class="max-width">
      <el-tabs type="border-card" v-model="activeName">
        <el-tab-pane label="Kategoria 1" name="first"><QuestionContainer /> </el-tab-pane>
        <el-tab-pane label="Kategoria 2" name="second">Kategoria 2</el-tab-pane>
        <el-tab-pane label="Kategoria 3" name="third">Kategoria 3</el-tab-pane>
        <el-tab-pane label="Kategoria 4" name="fourth">Kategoria 4</el-tab-pane>
      </el-tabs>
    </el-container>
  </div>
</template>

<script>
import QuestionContainer from './components/QuestionContainer'

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

<style>
.max-width {
  width: 400px;
}
</style>
