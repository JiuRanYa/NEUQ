<!--
组件参数：
1.title:要显示的标题，例如好课先看，type=String
2.imageSrc:图片目录，传入static下图片的文件目录
例如图片的目录为：static/images/index/content_icon.png,则imageSrc为"images/index/content_icon.png"
-->

<template name="index-title">
	<view class="content_title_wrapper">
		<image :src="images" mode=""></image>
		<view class="content_title">
			{{title}}
		</view>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				images:''
			}
		},
		name:"index-title",
		props: {
			title: {
				type: String,//属性类型
				value: "值"
			},
			imageSrc:{
				type: String,
				value:""
			}
		},
		//组件生命周期
		created() {
			let basic_src = "../../static/"
			let src = this.imageSrc
			this.images = basic_src + src;
		},
		methods: {
		}

	}
</script>

<style>
	.content_title_wrapper{
		display: flex;
		flex-direction: row;
	}
	.content_title_wrapper image{
		width: 60upx;
		height: 60upx;
		margin-top: 15upx;
		margin-left: 45upx;
	}
	.content_title_wrapper .content_title{
		font-size: 20px;
		margin: 15upx 15upx;
	}
</style>
