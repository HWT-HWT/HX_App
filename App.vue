<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
	.AllPage{
		width: 95%;
		margin: 0 auto;
		background-color: #fff;
		margin-top: 20rpx;
		border-radius: 20rpx;
		padding: 20rpx 0;
	}
	.All{
		width: 100vw;
		min-height:100vh;
		background-color: #f6f7fb;
	}
</style>
