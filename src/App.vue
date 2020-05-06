<template>
	<div id="app">
		<img src="./assets/logo.png">
		<div>
			<el-button @click="startHacking">Start</el-button>
		</div>
	</div>
</template>

<script>
	// 导入 NProgress 包对应的JS和CSS
	import NProgress from 'nprogress'
	import 'nprogress/nprogress.css'


	export default {
		methods: {
			async startHacking() {
				NProgress.start();

				const {
					data: res
				} = await this.$http.get("http://localhost/test/hello");

				this.$notify({
					title: 'OK',
					type: 'success',
					message: res,
					duration: 3000
				})

				NProgress.done();
			}
		}
	}
</script>

<style>
	#app {
		font-family: Helvetica, sans-serif;
		text-align: center;
	}
</style>
