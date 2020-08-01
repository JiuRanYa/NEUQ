<template>
	<view class="page page-fill">
		
		<!--搜索框start-->
		<view class="search_bar_study">
			<uni-search-bar :radius="100" placeholder="搜索" @confirm="search" ></uni-search-bar>
		</view>
		<!--搜索框end-->
		
		<!--轮播图start-->
		<view class="index_swiper">
			<swiper :indicator-dots="true" :autoplay="true" indicator-active-color="#FFFFFF" interval="2500">
				<swiper-item>
					<image src="../../static/images/index/index_swiper_class_1.png" mode=""></image>
				</swiper-item>
				<swiper-item>
					<image src="../../static/images/index/index_swiper_class_2.png" mode=""></image>
				</swiper-item>
				<swiper-item>
					<image src="../../static/images/index/index_swiper_class_3.png" mode=""></image>
				</swiper-item>
				<swiper-item>
					<image src="../../static/images/index/index_swiper_class_4.png" mode=""></image>
				</swiper-item>
			</swiper>
		</view>
		<!--轮播图end-->
		
		<!--选择导航start-->
		<view class="navbar_study ">
			<view class="flex-item">
				<view class="navbar_image_study" style="background-color: #caf0f8;">
					<image src="../../static/images/index/navbar_1.png" mode=""></image>
				</view>
				<text>笔记</text>
			</view>
			<view class="flex-item">
				<view class="navbar_image_study" style="background-color: #eae2b7;">
					<image src="../../static/images/index/navbar_2.png" mode=""></image>
				</view>
				<text>课程</text>
			</view>
			<view class="flex-item">
				<view class="navbar_image_study" style="background-color: #48cae4;">
					<image src="../../static/images/index/navbar_3.png" mode=""></image>
				</view>
				<text>班级</text>
			</view>
			<view class="flex-item">
				<view class="navbar_image_study" style="background-color: #90e0ef;">
					<image src="../../static/images/index/navbar_4.png" mode=""></image>
				</view>
				<text>动态</text>
			</view>
		</view>
		<!--选择导航end-->
		
		<!--好课先看start-->
		<view class="content_wrapper">
			<index-title title="好课先看" imageSrc="images/index/content_icon.png"></index-title>
			<view class="class_detail">
				<scroll-view scroll-x="true">
					<view class="scroll">
						<view class="class_recommand white_control">
							<view class="flex_control">
								<view class="class_command_type">
									<view class="class_type">计算机</view>
									<view class="class_total">共222节课</view>
								</view>
								
								<view class="class_recommand_detail">
									<image src="" mode="" class="class_image1"></image>
									<view class="class_recommand_title">
										<view class="class_title">
											算法设计
										</view>
										<view class="class_num">
											<image src="../../static/images/index/index_number.png" mode="" class="class_image2"></image>
											56414
										</view>
									</view>
								</view>
								<view class="class_recommand_detail">
									<image src="" mode="" class="class_image1"></image>
									<view class="class_recommand_title">
										<view class="class_title">
											JAVA程序设计
										</view>
										<view class="class_num">
											<image src="../../static/images/index/index_number.png" mode="" class="class_image2"></image>
											65416
										</view>
									</view>
								</view>
								<view class="class_recommand_detail">
									<image src="" mode="" class="class_image1"></image>
									<view class="class_recommand_title">
										<view class="class_title">
											网页设计入门
										</view>
										<view class="class_num">
											<image src="../../static/images/index/index_number.png" mode="" class="class_image2"></image>
											6548
										</view>
									</view>
								</view>
							</view>
						</view>
						
						<view class="class_recommand white_control">
							<view class="flex_control">
								<view class="class_command_type">
									<view class="class_type">英语</view>
									<view class="class_total">共222节课</view>
								</view>
								
								<view class="class_recommand_detail">
									<image src="" mode="" class="class_image1"></image>
									<view class="class_recommand_title">
										<view class="class_title">
											算法设计
										</view>
										<view class="class_num">
											<image src="../../static/images/index/index_number.png" mode="" class="class_image2"></image>
											5268
										</view>
									</view>
								</view>
							</view>
						</view>
						
						<view class="class_recommand white_control">
							<view class="flex_control">
								<view class="class_command_type">
									<view class="class_type">计算机</view>
									<view class="class_total">共222节课</view>
								</view>
								
								<view class="class_recommand_detail">
									<image src="" mode="" class="class_image1"></image>
									<view class="class_recommand_title">
										<view class="class_title">
											算法设计
										</view>
										<view class="class_num">
											<image src="../../static/images/index/index_number.png" mode="" class="class_image2"></image>
											5268
										</view>
									</view>
								</view>
							</view>
						</view>
						
						<view class="class_recommand white_control">
							<view class="flex_control">
								<view class="class_command_type">
									<view class="class_type">计算机</view>
									<view class="class_total">共222节课</view>
								</view>
								
								<view class="class_recommand_detail">
									<image src="" mode="" class="class_image1"></image>
									<view class="class_recommand_title">
										<view class="class_title">
											算法设计
										</view>
										<view class="class_num">
											<image src="../../static/images/index/index_number.png" mode="" class="class_image2"></image>
											5268
										</view>
									</view>
								</view>
							</view>
						</view>
					</view>
				</scroll-view>
			</view>
		</view>
		<!--好课先看end-->
		
		<view class="">
			<index-title title="好文欣赏" imageSrc="images/index/read.png"></index-title>
		</view>
	</view>
</template>

<script>
	
	export default {
		methods:{
			
		},
		data(){
			return{
				
			};
		},
		onLoad() {
			//轮播图数据请求
			/*
			uni.request({
			    url: 'https://www.imovietrailer.com/superhero/index/carousel/list', //仅为示例，并非真实接口地址。
			    method:"POST",
				success: (res) => {
			        console.log(res.data);
			        this.text = 'request success';
			    }
			});
			*/
		}
	}
</script>

<style>
	@import url("index.css");
</style>
