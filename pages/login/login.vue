<template>
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
					<text>注册账号</text>
				</view>
			</view>
		</form>
	</view>
</template>

<script>
	export default {
		data(){
			return{
				
			};
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
			}
		}
	}
</script>

<style>
	@import url("login.css");
</style>
