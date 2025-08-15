<template>
	<view class="account-Transfer">
		<view class="title">
			<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
			<view>
				<text>手机号转账</text>
				<image src="@/static/phone-transfer-1.png" mode=""></image>
			</view>
			<view class="right-icon">
				<view class="icon">
					<image src="@/static/server-1.png" mode=""></image>
				</view>
			</view>
		</view>
		
		<view class="remittance-box">
			<view class="remittance-list" v-for="(item,index) in transferBodyListOne" :key="index">
				<transferBodyVue :placeholder='item.placeholder' textAlign="left" :icon="item.imageIcon" :iconSize="item.iconSize"  v-model='item.value':array='index === 3 ?  transferBodyList[index].array : "" '>
					<template #text>
						{{item.name}} 
					</template>
				</transferBodyVue>
			</view>
		</view>
		
		<span style="color: #b78b3f; font-size: 20rpx; padding: 30rpx;">收款人姓名须为真实姓名</span>
		
		<view class="btn">
			下一步
		</view>
		
		<view class="OtherCards-tisi">
			<span>温馨提示:</span><br />
			<span>1、手机号转账单笔限额1万元，当日限额500万元</span> <br>
			<span>2、如收款人手机号码已绑定收款账户（绑定账户需收款人另行开通），则向该账户转账。</span><br />
			<span>3、如收款人手机号码未绑定收款账户，我行将通过短信发送您的转账申请，收款人可通过短信回复卡号转账；如收款人24小时未回复短信，交易自动取消。</span><br />
			<span>4、您如果需要将手机号绑定收款账户（他人即可通过您手机号向您直接转账），请进入【我的】—【设置】—【业务设置】—【手机号收付款设置】。</span> <br>
		</view>
		
		<view style="width: 100%; margin-top: 150rpx; text-align: center; color: #b78b3f; font-size: 28rpx;">为我的手机号绑定一张银行卡</view>
	</view>
</template>

<script>
	import transferBodyVue from '@/components/transfer-Body.vue'
	export default {
		data() {
			return {
				transferBodyListOne:[
					{
						placeholder:'请输入收款人户名',name:'姓名',imageIcon:'../../static/account-Transfer-icon-1.png', value:'', iconSize:'1.5'
					},
					{
						placeholder:'请输入收款人账号',name:'手机号码', value:'', iconSize:'1.5'
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
		background-color: #fff;
		padding: 40rpx 0;
		.title{
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			text-align: center;
			padding: 50rpx 30rpx;
			.left{
				width: 30rpx;
				height: 40rpx;
			}
			text{
				font-size: 35rpx;
				font-weight: bold;
			}
			view{
				display: flex;
			}
			image{
				width: 65rpx;
				height: 45rpx;
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
						width: 55rpx;
						height: 55rpx;
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
		.btn{
			width: 95%;
			margin: 0 auto;
			background-color:#d2d2d2 ;
			text-align: center;
			padding: 30rpx 0;
			border-radius: 5rpx;
			color: #fff;
			margin-top: 120rpx;
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
