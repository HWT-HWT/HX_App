<template>
	<view class="load-therr">
		<view class="load-title">
			<image class="left-icon" src="@/static/left-cion-1.png" mode=""></image>
			<text>我的贷款</text>
			<view class="icon">
				<image src="@/static/server-1.png" mode=""></image>
			</view>
		</view>
		<view class="load-View">
			<view class="host-view">
				<view class="textView">
					<view class="p"> 
						<p>个人经营性贷款</p>
					</view>
					<p class="span">400,000.00</p>
					<p class="text">获批额度(元)</p>
				</view>
				<view class="btnView" @click="GoDatali">
					查看详情
				</view>
			</view>
			<view class="Money-view">
				<view class="text-view">
					<p class="span">400,000.00</p>
					<p class="text">已用额度(元)</p>
				</view>
				<view class="text-view" style="border: none;">
					<p class="span">0.00</p>
					<p class="text">可用额度(元)</p>
				</view>
			</view>
		</view>
		<view class="load-Coupons" @click="Gojl">
			<view class="Coupons-view">
				<span>贷款记录</span>
			</view>
			<view class="Coupons-menu">
				<image src="@/static/upsdk_payment_right.webp" mode=""></image>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"load-therr",
		data() {
			return {
				
			};
		},
		methods:{
			Gojl(){
				uni.navigateTo({
					url:'/pages/load-JL/load-JL'
				})
			},
			GoDatali(){
				uni.navigateTo({
					url:'/pages/load-datali/load-datali'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
.load-therr{
	width: 100vw;
	min-height:100vh;
	background: url('../static/load-bg-1.png')no-repeat;
	background-size:100%;
	.load-title{
		padding: 50rpx 30rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		.left-icon{
			width: 35rpx;
			height: 45rpx;
		}
		text{
			font-size: 35rpx;
			font-weight: bold;
		}
		.icon{
			image{
				width: 65rpx;
				height: 65rpx;
			}
		}
	}
	.load-View{
		width: 95%;
		margin: 0 auto;
		background-color: #fff;
		margin-top: 20rpx;
		border-radius: 20rpx;
		.host-view{
			display: flex;
			align-items: center;
			justify-content: space-between;
			.textView{
				padding: 30rpx;
				.p{
					
					display: flex;
					align-items: center;
					p{
						font-weight: bold;
						font-size: 32rpx;
					}
				}
				.text{
					font-size: 25rpx;
					margin: 20rpx auto;
					color: #888;
				}
				.span{
					font-weight: bold;
					font-size: 50rpx;
					margin-top: 20rpx;
				}
			}
			.btnView{
				padding:15rpx 20rpx;
				color: #fff;
				background-color: #ea192f;
				margin: 0 30rpx;
				font-size: 26rpx;
				border-radius: 50rpx;
			}
		}
		.Money-view{
			width: 95%;
			margin: 0 auto;
			text-align: center;
			padding: 40rpx 0;
			border-top: 1px solid #ddd;
			display: flex;
			.text-view{
				width: 50%;
				border-right: 1px solid #ddd;
				padding:0 20rpx;
				.span{
					font-weight: bold;
					font-size: 40rpx;
				}
				.text{
					color: #888;
					font-size: 25rpx;
				}
			}
			
		}
	}
	.load-Coupons{
		width: 95%;
		margin: 0 auto;
		border-radius: 20rpx;
		background-color: #fff;
		display: flex;
		justify-content: space-between;
		margin-top: 40rpx;
		.Coupons-view{
			padding: 30rpx;
			align-items: center;
			display: flex;
			span{
				font-weight: bold;
				font-size: 32rpx;
			}
		}
		.Coupons-menu{
			padding: 20rpx 10rpx;
			display: flex;
			align-items: center;
			image{
				margin-top: 5rpx;
				width: 50rpx;
				height: 50rpx;
			}
		}
	}
}
</style>