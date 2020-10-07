<template>
	<view class="page">
		<view class="title">手机号注册</view>
		<view class="regsister_wrapper">
			<form @submit="handleSumbit" @reset="">
				<view class="auth_wrapper">
					<view class="item_title">电话</view>
					<input name='phone' type="number" @blur='getPhone' value="" placeholder="请输入手机号" confirm-type="next"/>
				</view>
				<view class="auth_wrapper">
					<view class="item_title">验证码</view>
					<input name='vaildCode' type="number" value="" placeholder="验证码" confirm-type="next" />
					<button class="auth_btn" :disabled="isdisabled" type="default" hover-stay-time='60000' hover-class="auth_btn_hover" @click="handleAuthCodeClick">{{btn_data}}</button>
				</view>
				<view class="auth_wrapper">
					<view class="item_title">密码</view>
					<input name='res_psw' type="password" value="" placeholder="请设置6-16位密码" confirm-type="next" />
				</view>
				<button class="comfirm_btn" type="default" form-type="submit">注册并登录</button>
				<view class="server">
					用户注册即代表同意《服务条款》
				</view>
			</form>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				phoneNumber:'',
				btn_data:'发送验证码',
				isdisabled:false,
				codeTime:60
			}
		},
		methods:{
			getPhone(e){
				this.phoneNumber = e.detail.value;
			},
			handleAuthCodeClick(e){
				let codeTime = ()=>{
					if(this.codeTime){
						this.codeTime--
						setTimeout(codeTime,1000)
						this.btn_data = this.codeTime + '秒后重试'
						this.isdisabled = true;
					}else{
						this.btn_data = '发送验证码'
						this.isdisabled = false;
					}
				}
				codeTime();
				uni.request({
					url:`http://127.0.0.1:3000/users/sendCode?phone=${this.phoneNumber}`,
					method:'POST'
				})
			},
			handleSumbit(e){
				let phone = e.detail.value.phone
				let code = e.detail.value.vaildCode 
				let psw = e.detail.value.res_psw
				
				console.log(phone,code)
				let url = `http://127.0.0.1:3000/users/vaildPhone?phone=${phone}&code=${code}`
				uni.request({
					url:url,
					method:'POST',
					data:{
						'psw':psw
					},
					success(res) {
						if(res.data.status == 200){
							let userInfo = res.data;
							console.log(userInfo)		
							uni.setStorageSync('globalUser',userInfo);
							console.log("设定缓存成功")
							uni.showToast({
								title:'注册成功'
							})
							setTimeout(function(){
								uni.switchTab({
									url:'../me/me'
								})
							},1500)
						}
					}
				})
			}
		}
	}
</script>

<style>
	@import url("res.css");
</style>
