<script>
//获取用户信息
global.getUserInfo = function(key){
	let userInfo = uni.getStorageSync("globalUser")
	if(userInfo == ''){
		console.log(userInfo + "userInfo")
		return null;
	}else{
		console.log(userInfo)
		return userInfo;
	}
}
//
global.phone_process = function(){
	if(global.getUserInfo()){
		let phone = global.getUserInfo().data[0].user_phone;
		let process_phone = phone.substr(0,3) + '****' + phone.substr(7,10)
		return process_phone;
	}

}
export default {
	onLaunch: function() {
		console.log('App Launch');
	},
	onShow: function() {
		console.log('App Show');
	},
	onHide: function() {
		console.log('App Hide');
	}
};
</script>

<style>
	uni-page-wrapper{
		background-color: #f7f7f7;
	}
	.page-fill{
		width: 100%;
		height: 100%;
	}
	.white_control{
		background-color: #FFFFFF;
	}
</style>
