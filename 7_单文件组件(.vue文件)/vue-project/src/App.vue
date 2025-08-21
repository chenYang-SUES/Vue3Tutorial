<template>
  <h1 class="title">我是根组件{{ msg }}</h1>
  <button @click="doClick">按钮</button>
  <MyChild></MyChild>
  <my-child></my-child>
</template>

<script>
  import MyChild from './pages/MyChild.vue';
  export default {
    data() {
      return {
        msg: "hahaha"
      }
    },
    methods: {
      doClick() {
        alert(1)
      }
    },
    components: {
      MyChild
    }
  }
</script>

<!-- scoped让样式只在当前组件内生效 -->
<style scoped>
  .title {
    color: red;
  }
</style>