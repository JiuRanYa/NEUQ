<template>
	<view class="">
		<view class="logo">
			<image src="../../static/images/me/avatar.png"></image>
		</view>

		<view class="login_form">
			<form @submit="" @reset="">

				<input type="text" value="" placeholder="邮箱/手机号" />
				<input type="text" value="" placeholder="密码" />
				<button class="btn" type="mini" form-type="submit">登录</button>
				<navigator url="../regsister/regsister" open-type="navigate" class="regsister">没有账号?点击注册</navigator>
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
	
</script>

<style>
	@import url("./login.css");
</style>
