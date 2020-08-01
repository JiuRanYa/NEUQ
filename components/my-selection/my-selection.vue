<template name='my-selection'>
	<view>
		<view class="mySelector_wrapper">
			<image :src="images" mode="" class="icon"></image>
			<view class="Selector_title">
				{{mytitle}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:'my-selection',
		data() {
			return {
				images:'',
				mytitle:''
			};
		},
		props:{
			imageSrc:{
				type:String,
				value:''
			},
			title:{
				type:String,
				value:''
			}
		},
		created(){
			this.mytitle = this.title;
			let basic_src = "../../static/"
			this.images = basic_src + this.imageSrc;
		}
	}
</script>

<style>
		.mySelector_wrapper{
			width: 100%;
			height: 120upx;
			display: flex;
			flex-direction: row;
			align-items: center;
			padding-left: 20px;
		}
		.icon{
			height: 70rpx;
			width: 70rpx;
		}
		.Selector_title{
			margin-left: 10px;
			color: #777777;
		}

</style>
