<template>
	<view class="page page-fill">
		<view class="header">
			<view v-if="userIsLogin" @click="useInfo">
				<image src="../../static/images/me/avatar.png" mode="" class="avatar" ></image>
			</view>
			<view v-else>
				<image src="../../static/images/me/default_avatar.png" mode="" class="avatar"></image>
			</view>
			
			<view class="info_wrapper" v-if="userIsLogin">
					<view class="nickname">
						久染
					</view>
					<view class="nav_info">
						132****5842
					</view>
			</view>
			<view class="info_wrapper" v-else>
				<navigator url="../login/login">
					<view class="nickname regs_login">
						注册/登录
					</view>
				</navigator>
			</view>
			
		</view>
		<splitLine color='#CDE6CB'></splitLine>
		<my-selection title="我的收藏" imageSrc="images/me/favorites.png"></my-selection>
		<my-selection title="历史记录" imageSrc="images/me/records.png"></my-selection>
		<my-selection title="我的好友" imageSrc="images/me/friends.png"></my-selection>
		<my-selection title="关于我们" imageSrc="images/me/aboutUs.png"></my-selection>
		<my-selection title="设置" imageSrc="images/me/setting2.png"></my-selection>
	</view>
</template>

<script>
	export default {
		comments:{
		},
		data(){
			return{
				userIsLogin:true
			};
		},
		methods: {
			useInfo(){
				uni.navigateTo({
					url:'../meInfo/meInfo'
				})
			}
		}
	}
</script>

<style>
	@import url("me.css");
</style>
