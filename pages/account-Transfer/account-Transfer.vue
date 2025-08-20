<template>
	<view class="account-Transfer">
		<view class="title">
			<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
			<text>转账</text>
			<view class="right-icon">
				<view class="icon">
					<image src="@/static/server-1.png" mode=""></image>
					<span>客服</span>
				</view>
				<view class="icon">
					<image src="@/static/server-1.png" mode=""></image>
					<span>客服</span>
				</view>
			</view>
		</view>
		
		<view class="remittance-box">
			<p>收款人</p>
			<view class="remittance-list" v-for="(item,index) in transferBodyListOne" :key="index">
				<transferBodyVue :placeholder='item.placeholder' :icon="item.imageIcon" :iconSize="item.iconSize"  v-model='item.value':array='index === 3 ?  transferBodyList[index].array : "" '>
					<template #text>
						{{item.name}} 
					</template>
				</transferBodyVue>
			</view>
		</view>
		
		<view class="CommonPayee-money">
			<view class="CommonPayee-title">
				<text class="text">转账金额</text>
				<text style="color: dodgerblue;">限额</text>
			</view>
			<view class="CommonPayee-list-box">
				<view class="list-content" style="border-bottom:1rpx solid #ddd;">
					<view class="image">
						￥
					</view>
					<view class="text">
						<input type="text" placeholder="0手续费" placeholder-style="color:#ccc; font-size:35rpx; font-weight:normal;">
					</view>
				</view>
				<view class="money-account">
					<span>付款账户</span>
					<view class="accountName">
						<view class="listView">
							<p>华夏卡(尾号9323)</p>
							<span>可用余额￥33,759.98</span>
						</view>
						<image src="../../static/upsdk_payment_right.webp" mode=""></image>
					</view>
				</view>
			</view>
		</view>
	
		<view class="remittance-box">
			<view class="remittance-list" v-for="(item,index) in transferBodyListTwo" :key="index">
				<transferBodyVue :placeholder='item.placeholder' :icon="item.imageIcon" :iconSize="item.iconSize"  v-model='item.value':array='index === 3 ?  transferBodyList[index].array : "" '>
					<template #text>
						{{item.name}} 
					</template>
				</transferBodyVue>
			</view>
		</view>
		
		<view class="btn">
			下一步
		</view>
		
		<view class="OtherCards-tisi">
			<span>温馨提示:</span><br />
			<span>1、为保障您的财产安全和合法权益，切莫轻信以网购刷单、冒充公检法、领导或亲人朋友、代办大额信用卡和高额贷款、网购客服或快递退款、鼓吹大额投资理财等非正规渠道要求进行的转账汇款，谨防被骗。涉及不明资金的转账事宜，务必当面或电话确认核实。</span> <br>
			<span>2、不扫描可疑二维码，不安装不明APP，妥善保管卡号、密码、短信验证码、令牌动态口令等个人重要信息。</span>
		</view>
	</view>
</template>

<script>
	import transferBodyVue from '@/components/transfer-Body.vue'
	export default {
		data() {
			return {
				transferBodyListOne:[
					{
						placeholder:'请输入收款人户名',name:'户名',imageIcon:'../../static/account-Transfer-icon-1.png', value:'', iconSize:'1.5'
					},
					{
						placeholder:'请输入收款人账号',name:'账户',imageIcon:'../../static/account-Transfer-icon-2.png', value:'', iconSize:'1.5'
					},
				],
				transferBodyListTwo:[
					{
						placeholder:'选填',name:'短信通知', value:'预计实时到账', iconSize:'1.5',imageIcon:'../../static/upsdk_payment_right.webp',
					},
					{
						placeholder:'可不填',name:'到账时间', value:'', iconSize:'1.5'
					},
					{
						placeholder:'选填',name:'短信通知', value:'', iconSize:'1.5',imageIcon:'../../static/upsdk_payment_right.webp',
					},
				],
			};
		},
		components:{
			transferBodyVue
		},
		methods:{
			back(){
				uni.navigateBack()
			}
		}
	}
</script>

<style lang="scss" scoped>
	.account-Transfer{
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
		.remittance-box{
			width: 95%;
			margin: 0 auto;
			border-radius: 20rpx;
			background-color: #fff;
			margin-top: 20rpx;
			p{
				padding-left: 30rpx;
				padding-top: 20rpx;
				font-weight: bold;
				font-size: 35rpx;
			}
		}
		.CommonPayee-money{
			width: 95%;
			margin: 0 auto;
			margin-top:20rpx;
			background-color: #fff;
			border-radius: 20rpx;
			.CommonPayee-title{
				width: 90%;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				align-items: center;
				background-color: #fff;
				padding-top: 30rpx;
				.text{
					font-weight: bold;
					font-size: 35rpx
				}
			}
			.CommonPayee-list-box{
				width: 100%;
				margin: 0 auto;
				background-color: #fff;
				border-radius: 20rpx;
				.list-content{
					width: 90%;
					margin: 0 auto;
					display: flex;
					align-items: center;
					margin-top: 30rpx;
					padding-bottom: 20rpx;
					font-size: 30rpx;
					.image{
						display: flex;
						align-items: center;
						font-size: 50rpx;
						font-weight: bold;
					}
					.text{
						flex: 1;
						margin-left: 20rpx;
						input{
							font-size: 50rpx;
							font-weight: bold;
						}
					}
				}
				.money-account{
					display: flex;
					justify-content: space-between;
					padding: 30rpx 40rpx;
					span{
						font-size: 32rpx;
					}
					.accountName{
						display: flex;
						align-items: center;
						.listView{
							text-align: right;
							p{
								font-size: 30rpx;
								font-weight: bold;
								padding-bottom: 5rpx;
							}
							span{
								font-size: 25rpx;
							}
						}
						image{
							width: 50rpx;
							height: 50rpx;
							margin-left: 10rpx;
						}
					}
				}
			}
		}
		.btn{
			width: 95%;
			margin: 0 auto;
			background-color:#eeb2b8 ;
			text-align: center;
			padding: 30rpx 0;
			border-radius: 50rpx;
			color: #fff;
			margin-top: 20rpx;
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
