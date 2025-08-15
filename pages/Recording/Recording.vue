<template>
	<view class="Recording">
		<view class="title">
			<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
			<text>转账记录查询</text>
			<view class="right-icon">
			</view>
		</view>
		<view class="taber">
			<view class="taber-View">
				<span>全部</span>
				<image src="@/static/recording-1.png" mode=""></image>
			</view>
			<view class="taber-View">
				<span>本月</span>
				<image src="@/static/recording-1.png" mode=""></image>
			</view>
		</view>
		<view class="input">
			<image src="@/static/Recording-seach-1.png" mode=""></image>
			<input type="text" placeholder="输入收款人姓名/账户/手机号/收款银行/附言搜索" />
		</view>
		<view class="image">
			<image src="@/static/load-bg-3.png" mode=""></image>
		</view>
		
		<view class="OtherCards-tisi">
			<span>温馨提示:</span><br />
			<span>1、您可以选择银行卡、交易时间，查询该银行卡在所选交易时间段的转账记录，如需进一步筛选，还可输入收款人姓名、收款账号、收款人手机号、收款银行、转账附言搜索。</span> <br>
			<span>2、此功能支持查询从2021年6月1日开始的记录，每次查询的时间跨度不得超过1年。</span>
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
		},
		methods:{
			back(){
				uni.navigateBack()
			}
		}
	}
</script>

<style lang="scss" scoped>
.Recording{
	width: 100vw;
	height: 100vh;
	background-color: #f5f7fa;
	.title{
		width: 100%;
		margin: 0 auto;
		background-color: #fff;
		padding-top: 100rpx;
		padding-bottom: 30rpx;
		padding-left: 30rpx;
		padding-right: 30rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		text-align: center;
		.left{
			width: 30rpx;
			height: 40rpx;
		}
		text{
			font-size: 35rpx;
			margin-left: -100rpx;
		}
		.right-icon{
			display: flex;
			right: 100rpx;
			.icon{
				display: flex;
				align-items: center;
				justify-content: center;
				flex-wrap: wrap;
				text-align: center;
				image{
					width: 50rpx;
					height: 50rpx;
				}
				span{
					width: 100%;
					font-size: 20rpx;
					margin-top: -5rpx;
				}
			}
		}
	}
	.taber{
		display: flex;
		justify-content: space-evenly;
		background-color: #fff;
		padding: 20rpx 0;
		.taber-View{
			width: 30%;
			display: flex;
			justify-content: center;
			align-items: center;
			image{
				width: 28rpx;
				height: 20rpx;
				margin: 0 10rpx;
			}
		}
	}
	.input{
		width: 90%;
		margin: 0 auto;
		margin-top: 20rpx;
		padding: 15rpx 25rpx;
		border-radius: 10rpx;
		background-color: #fff;
		display: flex;
		align-items: center;
		image{
			width: 40rpx;
			height: 40rpx;
		}
		input{
			flex: 1;
			font-size: 25rpx;
			margin-left: 20rpx;
		}
	}
	.image{
		width: 100%;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-top: 150rpx;
		image{
			width: 320rpx;
			height: 300rpx;
		}
	}
	.OtherCards-tisi{
		width: 90%;
		margin: 0 auto;
		margin-top: 50rpx;
		span{
			font-size: 25rpx;
			color: #888;
		}
	}
}
</style>
