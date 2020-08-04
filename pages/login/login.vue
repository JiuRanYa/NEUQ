<template>
	<!--
	<view class="page-fill">
		<form @submit="formSubmit" @reset="" >
			<view class="center_control">
				<view class="login_title center_control">
					Login
				</view>
				<view class="info">
					<input class="info_input" name='username' type="text" value="" placeholder="请输入账号"/>
					</input>
				</view>
				<view class="info">
					<input class="info_input" name='password' type="password" value="" placeholder="请输入密码"/></input>
				</view>
				<button form-type="submit" class="submit_btn">登录</button>
				<view class="login_bottom">
					<text>忘记密码</text>
					<view class="">|</view>
					<text @click="router_res">注册账号</text>
				</view>
			</view>
		</form>
	</view>
	-->
		<view class="">
			<view class="logo">
				<image src="../../static/images/me/avatar.png"></image>
			</view>
	
			<view class="login_form">
				<form @submit="formSubmit" @reset="">
					<input name='username' type="text" value="" placeholder="邮箱/手机号" />
					<input name='password' type="password" value="" placeholder="密码" />
					<button class="btn" type="mini" form-type="submit">登录</button>
					<navigator url="../regsister/res" open-type="navigate" class="regsister">没有账号?点击注册</navigator>
				</form>
			</view>
			<view class="oauth_wrapper" >
				<view class="oauth_title">--- 第三方登录 ---</view>
				<view class="oauth_img">
					<image data-type="qq" v-if="hasProvider" src="../../static/images/login/QQ.png" mode="" @click="handleClick"></image>
					<image data-type="github" src="../../static/images/login/github.png" @click="handleClick" mode=""></image>
				</view>
			</view>
	
		</view>
</template>

<script>
	export default {
			data() {
				return {
				hasProvider:false
				};
			}	,
			onLoad(){
				this.initProvider()
			},
			methods:{
				formSubmit(e){
					let username = e.detail.value.username;
					let password = e.detail.value.password;
					
					uni.request({
						url:'http://localhost:3000/users/login',
						method:'POST',
						data:{
							"username":username,
							"password":password
						},
						success(res) {
							
							if(res.data.status == 200){
								let userInfo = res.data;
								console.log(userInfo)
								uni.setStorageSync('globalUser',userInfo);
								uni.switchTab({
									url:'../me/me'
								})
							}else if(res.data.status != 200){
								uni.showToast({
									title:res.data.msg,
									duration:2000,
									image:'../../static/images/login/error.png'
								})
							}
						},
						fail() {
							console.log("发送失败")
						}
					})
				},
				initProvider() {
					const filters =  ['qq'];
					uni.getProvider({
						service: 'oauth',
						success: (res) => {
							if (res.provider && res.provider.length) {
								for (let i = 0; i < res.provider.length; i++) {
									if (~filters.indexOf(res.provider[i])) {
										this.hasProvider = true;
									}
								}	
							}
						},
						fail: (err) => {
							console.error('获取服务供应商失败：' + JSON.stringify(err));
						}
					});
				},
				handleClick(e){
					uni.getProvider({
						 service: 'oauth',
						 success: (res) => {
						 	console.log(res)
						 }
					})
					let type = e.currentTarget.dataset.type;
					uni.login({
						"provider":type,
						success:(res)=>{
							const openid = res.authResult.openid;
							const access_token = res.authResult.access_token
						},
						fail: (err) => {
							console.log(err)
						}
					})
				}
			}
		}
	
	/*
	export default {
		data(){
			return{
				
			};
		},
		methods:{
			router_res(){
				uni.navigateTo({
					url: '../regsister/res',
					success: res => {},
					fail: () => {},
					complete: () => {}
				})
			},
			formSubmit(e){
				let username = e.detail.value.username;
				let password = e.detail.value.password;
				
				uni.request({
					url:'http://localhost:3000/users/login',
					method:'POST',
					data:{
						"username":username,
						"password":password
					},
					success(res) {
						
						if(res.data.status == 200){
							let userInfo = res.data;
							console.log(userInfo)
							uni.setStorageSync('globalUser',userInfo);
							uni.switchTab({
								url:'../me/me'
							})
						}else if(res.data.status != 200){
							uni.showToast({
								title:res.data.msg,
								duration:2000,
								image:'../../static/images/login/error.png'
							})
						}
					},
					fail() {
						console.log("发送失败")
					}
				})
			}
		}
	}*/
</script>

<style>
	@import url("login.css");
</style>
