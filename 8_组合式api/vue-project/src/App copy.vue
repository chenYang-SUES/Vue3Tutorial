<template>
  <h1>{{ msg }}</h1>
  <button @click="fn">按钮</button>
</template>

<script>

  export default {
    setup() {
      // setup是生命周期函数，在组件创建之前执行
      // 因此setup中访问不到this
      console.log(this)  // undefined

      // 在局部作用域中定义变量、方法、计算属性、侦听等
      let msg = "hello"
      const fn = () => console.log("haha")

      // 返回对象，页面用到什么返回什么
      return {
        msg,
        fn
      }

    }

  }
</script>

<style scoped></style>