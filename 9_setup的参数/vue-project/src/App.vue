<template>
	<h1>我是根组件</h1>
	<MyChild a="我是父组件的数据" b="我是父组件的另一条数据" @myevent="handleMyEvent">
		<template #before>
			<h3>今天天气不错1111</h3>
		</template>
		<template #after>
			<h3>今天天气不错</h3>
		</template>
	</MyChild>
</template>

<script>
	import MyChild from './pages/MyChild.vue';


	export default {
		setup() {
			const handleMyEvent = (data) => {
				console.log(data)
			}
			return {
				handleMyEvent
			}
		},
		components: {
			MyChild
		}
	}
</script>

<style scoped></style>