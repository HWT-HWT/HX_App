<template>
	<view class="account-datali">
		<view class="title">
			<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
			<text>账户详情</text>
			<view class="right-icon">
				<view class="icon">
					<image src="@/static/server-1.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="account-card">
			<view class="card-Uname">
				<view class="Uname">
					<image src="../../static/account-datali-icon-1.png" mode=""></image>
					<view>
						<view class="eye">
							<text>6230 **** **** 9323</text>
							<image src="../../static/boc_finance_eye_close-white.png" mode=""></image>
						</view>
						<span>借记卡(I) | 华夏卡</span>
					</view>
				</view>
			</view>
			<view class="card-data">
				<text>华夏银行股份有限公司广州分行营业部</text>
				<span>开户日期:2022-06-29</span>
			</view>
		</view>
		<view class="money">
			<view class="title">资产</view>
			<view class="money-box">
				<span>存款</span>
				<view class="icon">
					<text>33,759.98</text>
					<image src="../../static/upsdk_payment_right.webp" mode=""></image>
				</view>
			</view>
		</view>
		<view class="index-listview">
			<ListViewVue :list="ListView" BoxWodth="25%" width="80" height="80" font-size="28rpx" @index="getListIindex"></ListViewVue>
			<view class="listview-menu">
				<span>更多服务</span>
				<image src="../../static/upsdk_payment_right.webp" mode=""></image>
			</view>
		</view>
		<view class="image">
			<image src="@/static/account-image-1.png" mode=""></image>
		</view>
	</view>
</template>

<script>
	import ListViewVue from '../../components/ListView.vue';
	export default {
		data() {
			return {
				ListView:[
					{name:'储蓄国债',images:'../../static/account-list-icon-1.png'},
					{name:'卡设置',images:'../../static/account-list-icon-2.png'},
					{name:'理财',images:'../../static/account-list-icon-3.png'},
					{name:'转账',images:'../../static/account-list-icon-4.png'},
					{name:'收支账单',images:'../../static/account-list-icon-5.png'},
					{name:'即使收款',images:'../../static/account-list-icon-6.png'},
					{name:'非柜面支付管理',images:'../../static/account-list-icon-7.png'},
					{name:'基金',images:'../../static/account-list-icon-8.png'},
				],
			};
		},
		methods:{
			back(){
				uni.navigateBack()
			},
			getListIindex(index){
				index == 3 ? uni.navigateTo({
					url:'/pages/TransferPage/TransferPage'
				})  : '' 
				index == 4 ? uni.navigateTo({
					url:'/pages/IncomeExpenses/IncomeExpenses'
				})  : '' 
			}
		},
		components:{
			ListViewVue
		}
	}
</script>

<style lang="scss" scoped>
	.account-datali{
		margin: 0 auto;
		min-height: 100vh;
		background-color: #f5f5f5;
		.title{
			background-color: #fff;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			text-align: center;
			padding: 0 30rpx;
			padding-top: 100rpx;
			padding-bottom: 30rpx;
			.left{
				width: 35rpx;
				height: 45rpx;
			}
			text{
				font-size: 35rpx;
				color: #222;
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
						width:55rpx;
						height:55rpx;
					}
					span{
						width: 100%;
						font-size: 20rpx;
						margin-top: -5rpx;
					}
				}
			}
		}
		.account-card{
			width: 95%;
			margin: 0 auto;
			padding: 20rpx 0;
			margin-top: 30rpx;
			background: url('@/static/account-datali-bg-1.png');
			background-size: 100% 100%;
			border-radius: 20rpx;
			color: #fff;
			.card-Uname{
				padding: 20rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				.Uname{
					display: flex;
					align-items: center;
					image{
						width: 80rpx;
						height: 80rpx;
						margin-right: 20rpx;
					}
					span{
						font-size: 23rpx;
						color: #f4c2c7;
					}
					.eye{
						display: flex;
						align-items: center;
						margin-bottom: -10rpx;
						text{
							font-size: 38rpx;
							font-weight: bold;
						}
						image{
							margin: 10rpx 30rpx;
							width: 40rpx;
							height: 40rpx;
						}
					}
				}
				
			}
			
			.card-data{
				padding: 30rpx;
				display: flex;
				align-items: center;
				flex-wrap: wrap;
				text{
					font-size: 32rpx;
					font-weight: bold;
				}
				span{
					width: 100%;
					color: #f4c2c7;
					font-size: 25rpx;
					margin-top: 10rpx;
				}
			}
		}
		.money{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius:20rpx;
			.title{
				padding: 40rpx 0 0 30rpx;
				border-radius:20rpx;
				font-size: 32rpx;
				font-weight: bold;
			}
			.money-box{
				display: flex;
				padding: 30rpx;
				align-items: center;
				justify-content: space-between;
				span{
					font-size: 32rpx;
				}
				.icon{
					display: flex;
					align-items: center;
					text{
						font-weight: bold;
						font-size: 35rpx;
					}
					image{
						width: 48rpx;
						height: 48rpx;
					}
				}
			}
		}
		.index-listview{
			width: 95%;
			border-radius: 20rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			padding: 30rpx 0;
			background-color: #fff;
			.listview-menu{
				display: flex;
				align-items: center;
				justify-content: center;
				margin-top: 50rpx;
				span{
					font-size:28rpx;
				}
				image{
					width: 45rpx;
					height: 45rpx;
				}
			}
		}
		.image{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			image{
				width: 100%;
				height: 200rpx;
			}
		}
	}
</style>
