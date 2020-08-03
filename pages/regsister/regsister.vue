<template>
	<view class="">
		<view class="title">手机号注册</view>
		<view class="regsister_wrapper">
			<form @submit="handleSumbit" @reset="">
				<view class="auth_wrapper">
					<view class="item_title">电话</view>
					<input type="number" value="" placeholder="请输入手机号" confirm-type="next" @input="handleNumberChange"/>
				</view>
				<view class="auth_wrapper">
					<view class="item_title">验证码</view>
					<input type="number" value="" placeholder="验证码" confirm-type="next" />
					<button class="auth_btn" type="default" @click="handleAuthCodeClick">获取验证码</button>
				</view>
				<view class="auth_wrapper">
					<view class="item_title">密码</view>
					<input type="number" value="" placeholder="请设置6-16位密码" confirm-type="next" />
				</view>
				<button class="comfirm_btn" type="default">注册并登录</button>
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
				phoneNumber:''
			}
		},
		method:{
			handleNumberChange(e){
				const value = e.detail.value;
				this.phoneNumber = value
			}
			,
			handleAuthCodeClick(e){
				
			}
		}
	}
</script>

<style>
	@import url("regsister.css");
</style>
