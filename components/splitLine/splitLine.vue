<!--
组件参数：
color：分割线的颜色 
eg:	color='#FFFFFF',type=String
-->



<template name='splitLine'>
	<view class="split_line" :style="bgColor" v-if="color"></view>
	<view class="split_line" style="background-color: #EBF6F6;" v-else></view>
</template>

<script>
	export default {
		name:'splitLine',
		data() {
			return {
				bgColor:''
			};
		},
		props:{
			color:{
				type:String,
				value:'#EBF6F6'
			}
		},
		created() {
			let bgColorCom = 'background-color:'
			this.bgColor = bgColorCom + this.color
		}

	}
</script>

<style>
	.split_line{
		width: 100%;
		height: 50upx;
	}
</style>
