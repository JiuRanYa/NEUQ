<template>
	<view class="page">
		<view class="user_avatar">
			<view class="user_avatar_title">
				头像
			</view>
			<view class="user_avatar_avatar">
				<image src="../../static/images/me/avatar.png" mode=""></image>
				<image src="../../static/images/me/setting.png" mode=""></image>
			</view>
		</view>
		<splitLine></splitLine>
		<view class="options">
			<view class="options_title">
				昵称
			</view>
			<view class="options_nickname font-control">
				久染
			</view>
		</view>
		<view class="options">
			<view class="options_title">
				性别
			</view>
			<view class="sex_picker">
				<picker mode="selector" :range="sex_options" @change="bindPickerChange" :value="index">
					<view class="uni-input font-control">{{sex_options[index]}}</view>
				</picker>
			</view>
		</view>
		<view class="options">
			<view class="options_title">
				生日
			</view>
			<view class="birth_picker">
				<picker mode="date" :value="date" :start="startDate" :end="endDate" @change="bindDateChange">
					<view class="uni-input font-control">{{date}}</view>
				</picker>
			</view>
		</view>
		
		<view class="options">
			<view class="options_title">
				签名
			</view>
			<input class="font-control" type="text" value="我是一个没有脑袋的佩奇" />
		</view>
		
		<view class="options">
			<view class="options_title">
				手机号
			</view>
			<view class="font-control">
				132****5413
			</view>
		</view>
		<splitLine></splitLine>
		<view class="options">
			<view class="options_title">
				我的二维码
			</view>
		</view>
	</view>
</template>

<script>	
	import splitLine from '../../components/splitLine/splitLine';
	export default{
		comments:{
			splitLine
		},
		data(){
			const currentDate = this.getDate({
				format: true
			})
			return{
				sex_options:["男","女"],
				index:0,
				date: currentDate,
			}
		},
		computed: {
			startDate() {
				return this.getDate('start');
			},
			endDate() {
				return this.getDate('end');
			}
		},
		methods:{
			bindPickerChange(e){
				this.index = e.target.value;
			},
			bindDateChange(e) {
				this.date = e.target.value
			},
			getDate(type) {
				const date = new Date();
				let year = date.getFullYear();
				let month = date.getMonth() + 1;
				let day = date.getDate();
				if (type === 'start') {
					year = year - 60;
				} else if (type === 'end') {
					year = year + 2;
				}
				month = month > 9 ? month : '0' + month;;
				day = day > 9 ? day : '0' + day;
				return `${year}-${month}-${day}`;
			},
		}
	}
</script>

<style>
	@import url("meInfo.css");
</style>
