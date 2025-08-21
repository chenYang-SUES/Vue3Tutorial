<template>
    <h1>我是根组件</h1>
    <hr>
    <h1>{{ obj }}</h1>
    <button @click="doClick">reactive</button>
    <button @click="doClick2">reactive2</button>
    <hr>
    <h1>{{ obj2 }}</h1>
    <button @click="doClick3">ref</button>
    <button @click="doClick4">ref2</button>
</template>

<script>
    /*
        reactive: 专门处理数组和对象
            优点: js中读写不用调用value属性
            缺点: 
                - 数据类型有限
                - 不允许整体重新赋值
                    - reactive对象编程了一个响应式对象，ref把数据包裹在了一个响应式对象中(依靠团队)
    */
    import { reactive, ref } from 'vue';
    export default {
        setup() {
            let obj = reactive({ name: "坤坤", hobby: ["唱", "跳", "rap"], num: ref(1) })
            const doClick = () => {
                obj.hobby[2] = "打篮球"
                // ref作为响应式对象的属性也会自动解包, 否则不会
                console.log(obj.num)
            }
            const doClick2 = () => {
                obj = { name: "cyeext" }
                console.log(obj)
            }

            let obj2 = ref({ name: "坤坤", hobby: ["唱", "跳", "rap"] })
            const doClick3 = () => {
                obj2.value.hobby[2] = "打篮球"
            }
            const doClick4 = () => {
                obj2.value = { name: "cyeext" }
            }
            return {
                obj,
                doClick,
                doClick2,
                obj2,
                doClick3,
                doClick4
            }
        }
    }
</script>

<style scoped></style>