<template>
    <h1>我是根组件</h1>
    <!-- 4. 模板中会自动调用value属性(自动解包) -->
    <h1>{{ msg }}</h1>
    <button @click="doClick">按钮</button>
    <hr>
    <h1>{{ arr }}</h1>
    <button @click="doClick2">按钮</button>
    <hr>
    <h1>{{ obj }}</h1>
    <button @click="doClick3">按钮</button>
</template>

<script>
    import { ref } from 'vue';
    export default {
        setup() {
            // 1. 在选项式api的data配置项中定义的数据, 如果发生变化会导致视图的更新
            // 而在setup函数中, 普通变量的数据变化不会触发视图更新
            // let msg = "hello vue"
            // const doClick = () => {
            //     msg = "哈喽Vue3"
            //     console.log(msg)
            // }

            // 2. 通过ref函数处理的数据变成了一个响应式对象
            let msg = ref("hello vue")
            const doClick = () => {
                // 3. 在js中读和改要调用对象的value属性
                msg.value = "哈喽Vue3"
                console.log(msg.value)
            }

            // 5. ref封装数组，数组元素的变化会触发视图更新
            const arr = ref([1, 2, [9, 0]])
            const doClick2 = () => {
                arr.value[0] = 100
                arr.value.push(8)
                arr.value[2][0] = 200
            }

            // 6. ref封装对象，对象元素的变化会触发视图更新
            const obj = ref({ name: "坤坤", hobby: ["唱", "跳", "rap"] })
            const doClick3 = () => {
                obj.value.hobby[2] = "打篮球"
            }
            return {
                msg,
                doClick,
                arr,
                doClick2,
                obj,
                doClick3
            }
        }
    }
</script>

<style scoped></style>