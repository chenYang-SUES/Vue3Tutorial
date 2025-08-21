<template>
    <div>
        <slot name="before"></slot>
        <h2>我是子组件 {{ a }}</h2>
        <slot name="after"></slot>
        <button @click="doClick">按钮</button>
    </div>
</template>

<script>
    /* 
        setup的参数:
            1. props
            2. context上下文对象，包含
                - emit 用来触发自定义事件 ※
                - attrs 用来接收props中没有声明的属性 
                - slots 拿到插槽的元素
                - expose
     */
    export default {
        props: ["a"],
        setup(props, context) {
            const doClick = () => {
                console.log(props.a)
                context.emit("myevent", "我是子组件的数据")
                // Proxy(Object) {b: '我是父组件的另一条数据', onMyevent: ƒ}

                console.log(context.slots)
            }
            return {
                doClick
            }
        }
    }
</script>

<style scoped></style>