<template>
	<view class="account">
		<view class="title">
			<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
			<text>我的账户</text>
			<view class="right-icon">
				<view class="icon">
					<image src="@/static/server-1.png" mode=""></image>
					<span>客服</span>
				</view>
				<view class="icon">
					<image src="@/static/server-2.png" mode=""></image>
					<span>我要开卡</span>
				</view>
			</view>
		</view>
		<view class="account-taber">
			<view class="taber" v-for="(item,index) in tabs" :key="index" @click="GetIndex(index)" :style="{fontWeight:index === tabIndex ? 'bold' :'normal',color:index === tabIndex ? '#000' :'#555'}">
				<span>{{item}}</span>
				<image :style="{opacity:index === tabIndex ? '1' :'0'}" src="@/static/account-taber-1.png" mode=""></image>
			</view>
		</view>
		<view class="account-card "v-if="tabIndex == 0">
			<view class="card-Uname">
				<view class="Uname">
					<span>借记卡(I) | 华夏卡</span>
					<view class="eye">
						<text>6230 **** **** 9324</text>
						<image src="../../static/boc_finance_eye_close.png" mode=""></image>
					</view>
				</view>
				<image src="../../static/account-icon-1.png" mode=""></image>
			</view>
			<view class="account-Money">
				<span>可用余额</span>
				<view class="money" @click="GoAccountDatali">
					<text>￥0.00</text>
					<image src="@/static/upsdk_payment_right.webp" mode=""></image>
				</view>
			</view>
			<view class="account-list">
				<view class="listView" v-for="(item,index) in accountList" :key="index">
					{{item}}
				</view>
			</view>
		</view>
		<view class="image" v-else>
			<image src="@/static/account-datali-bg-2.png" mode=""></image>
		</view>
		<view class="account-add">
			<span>+</span>
			<text>添加银行卡</text>
		</view>
		
		<view class="add">
			添加专享卡
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				tabs:['借记卡(1)','信用卡(0)'],
				tabIndex:0,
				accountList:['购买理财','转账','交易明细','卡设置']
			};
		},
		methods:{
			back(){
				uni.navigateBack()
			},
			GetIndex(index){
				this.tabIndex = index
			},
			GoAccountDatali(){
				uni.navigateTo({
					url:'/pages/account-datali/account-datali'
				})
			}
		}
	}
</script>

<style lang="scss" scoped>
	.account{
		margin: 0 auto;
		min-height: 100vh;
		background-color: #f5f5f5;
		padding: 40rpx 0;
		.title{
			width: 95%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			text-align: center;
			padding-top: 50rpx;
			padding-bottom: 20rpx;
			.left{
				width: 30rpx;
				height: 40rpx;
			}
			text{
				margin-left: 100rpx;
				font-size: 35rpx;
				font-weight: bold;
			}
			.right-icon{
				display: flex;
				.icon{
					margin-left: -20rpx;
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
		.account-taber{
			display: flex;
			margin-top: 20rpx;
			.taber{
				width: 150rpx;
				display: flex;
				flex-wrap: wrap;
				text-align: center;
				justify-content: center;
				align-items: center;
				margin-left: 20rpx;
				color: #555;
				span{
					font-size: 32rpx;
					width: 100%;
				}
				image{
					width: 40rpx;
					height: 20rpx;
				}
			}
		}
		.account-card{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background: url('@/static/account-bg-1.png');
			background-size: 100% 100%;
			border-radius: 20rpx;
			.card-Uname{
				padding: 20rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				.Uname{
					span{
						font-size: 28rpx;
						font-weight: bold;
					}
					.eye{
						display: flex;
						align-items: center;
						text{
							font-size: 26rpx;
						}
						image{
							margin: 10rpx 20rpx;
							width: 30rpx;
							height: 30rpx;
						}
					}
				}
				image{
					width: 80rpx;
					height: 40rpx;
				}
			}
			.account-Money{
				padding: 20rpx;
				display: flex;
				justify-content: space-between;
				span{
					color: #888;
				}
				.money{
					display: flex;
					align-items: center;
					font-size: 45rpx;
					font-weight: bold;
					image{
						width: 50rpx;
						height: 50rpx;
					}
				}
			}
			.account-list{
				display: flex;
				justify-content: space-between;
				padding: 30rpx;
				border-top: 1px solid #f3f3f3;
				.listView{
					width: 100rpx;
					text-align: center;
					background-color: #eef4fd;
					padding: 15rpx 20rpx;
					font-size: 25rpx;
					border-radius: 50rpx;
					color: #6ea2f1;
				}
			}
		}
		.image{
			width: 95%;
			margin: 0 auto;
			display: flex;
			justify-content: center;
			image{
				width: 450rpx;
				height: 500rpx;
			}
		}
		.account-add{
			display: flex;
			align-items: center;
			background-color: #fff;
			display: flex;
			justify-content: center;
			width: 95%;
			padding: 20rpx 0;
			margin: 0 auto;
			margin-top: 50rpx;
			border-radius: 20rpx;
			font-weight: bold;
			span{
				font-weight: normal;
				font-size: 50rpx;
				margin: 0 20rpx;
			}
		}
		.add{
			width: 100%;
			text-align: center;
			color:#6099ef;
			font-size: 30rpx;
			margin-top: 50rpx;
		}
	}	
</style>
