<script>
global.isLogin = function(){
	try{
		var suid = uni.getStorageSync('suid');
		var srand = uni.getStorageSync('srand');
	}catch(e){
		//TODO handle the exception
	}
	if(suid == '' || srand == ''){
		return false;
	}else{
		return [suid,srand];
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
	.page {
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
