<template>
	<view class="load-jl">
		<loadTitleVue title="贷款记录"></loadTitleVue>
		<view class="load-image">
			<image src="@/static/load-bg-3.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	import loadTitleVue from '../../components/load-title.vue';
	export default {
		data() {
			return {
				
			};
		},
		components:{
			loadTitleVue
		}
	}
</script>

<style lang="scss">
	.load-jl{
		width: 100vw;
		min-height:100vh;
		background-size:100%;
		background-color: #f5f7fa;
		
		.load-image{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			display: flex;
			justify-content: center;
			align-items: center;
			padding: 50rpx 0;
			image{
				width: 350rpx;
				height: 350rpx;
			}
		}
	}
</style>
