<template>
	<view class="IncomeExpenses">
		<view class="title">
			<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
			<view class="title-taber">
				<view class="taber" v-for="(item,index) in titleTaber" :key="index" @click="TbaIndex(index)">
					<text :style="{fontWeight:index === tabIndex ? 'bold' : 'normal'}">{{item}}</text>
					<view class="box" :style="{opacity:index === tabIndex ? '1' : '0'}"></view>
				</view>
			</view>
			<view class="right-icon">
				<view class="icon">
					<image src="@/static/server-1.png" mode=""></image>
				</view>
				<view class="icon">
					<image src="@/static/server-2.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="taber">
			<view class="tb" v-for="(item,index) in taber" :key="index" @click="getIndex(index)">
				<span v-if="index == 0">{{cardName || item}}</span>
				<span v-if="index == 1">{{date || item}}</span>
				<span v-if="index == 2">{{select || item}}</span>
				<image src="../../static/recording-1.png" mode="" v-if="index !== 2"></image>
			</view>
		</view>
		
		<IncomeExpensesTaberVue :selectIndex='selectIndex' @btn='btn' @data='data'></IncomeExpensesTaberVue>
		
		<view v-if="tabIndex == 0">
			<view class="IncomeExpenses-list" v-for="(item,index) in list" :key="index">
				<view class="listTitle">
					<view class="yesr">
						<text>{{item.Month}}</text>
						<view class="span">
							<span>{{item.Year}}</span>
						</view>
					</view>
					<view class="text-icon">
						<span>月账单</span>
						<image src="../../static/upsdk_payment_right.webp" mode=""></image>
					</view>
				</view>
				<span class="subTitle">{{item.money}}</span>
				<view class="list">
					<view class="li" v-for="(sum,num) in item.date" :key="num">
						<view class="date">
							<image src="../../static/index-icon-1.png" mode=""></image>
						</view>
						<view class="centent">
							<view class="centent-view">
								<view class="Left-View">
									<span>{{sum.title}}</span>
									<p>余额 {{sum.balance}}</p>
								</view>
								<view class="Right-View">
									<p> <text :style="{color: sum.color ? '#d8111c':'#000'}">{{sum.add}}</text></p>
									<view>华夏卡 {{sum.username}}</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="month" v-if="tabIndex == 1">
			<view class="month-box">
				<view class="box">
					<span>支出</span>
					<text>0.00</text>
				</view>
				<view class="box" style="background: #fff; color: #be9e67;" >
					<span>支出</span>
					<text>0.00</text>
				</view>
			</view>
			<view class="SubTitme">
				本月入不敷出,要注意节流开支奥~
			</view>
			<image src="@/static/IncomeExpenses-bg-1.png" mode=""></image>
		</view>
	</view>
	
</template>

<script>
	import IncomeExpensesTaberVue from '../../components/IncomeExpenses-taber.vue';
	export default {
		data() {
			return {
				titleTaber:['我的账户','月账单'],
				taber:['银行卡','2025-08','筛选'],
				tabIndex:0,
				list:[
					{
						Year:'2025年',
						Month:'7月',
						money:'支出￥0.00 收入 215.89',
						date:[
							{Day:'01',week:'周日',title:'贷款-扣收贷本息',balance:'07-20 周日 02:19',username:'0.00',add:'-6,518.09',color:false},
						],
					},
					{
						Year:'2025年',
						Month:'6月',
						money:'支出￥0.00 收入 215.89',
						date:[
							{Day:'01',week:'周日',title:'贷款-扣收贷本息',balance:'07-20 周日 02:19',username:'0.00',add:'-43,866.67',color:false},
						],
					},
					{
						Year:'2025年',
						Month:'5月',
						money:'支出￥0.00 收入 215.89',
						date:[
							{Day:'01',week:'周日',title:'贷款-扣收贷本息',balance:'07-20 周日 02:19',username:'0.00',add:'-43,866.67',color:false},
						],
					},
					{
						Year:'2025年',
						Month:'5月',
						money:'支出￥0.00 收入 215.89',
						date:[
							{Day:'01',week:'周日',title:'贷款-扣收贷本息',balance:'07-20 周日 02:19',username:'0.00',add:'-43,866.67',color:false},
						],
					},
					
				],
				selectIndex:999,
				cardName:'银行卡',
				date:'2025-08',
				select:'筛选'
			};
		},
		methods:{
			TbaIndex(index){
				this.tabIndex = index
			},
			back(){
				uni.navigateBack()
			},
			getIndex(index){
				this.selectIndex = index
			},
			btn(res){
				var index = res[1]
				this.cardName = res[0][index]
				this.selectIndex = 999
			},
			data(res){
				this.date = res,
				this.selectIndex = 999
			}
		},
		components:{
			IncomeExpensesTaberVue
		}
	}
</script>

<style lang="scss">
	.IncomeExpenses{
		margin: 0 auto;
		min-height: 100vh;
		background-color: #f5f5f5;
		.title{
			margin: 0 auto;
			margin-top: 80rpx;
			padding:30rpx;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			text-align: center;
			.left{
				width: 30rpx;
				height: 40rpx;
			}
			.title-taber{
				display: flex;
				margin-left: 50rpx;
				.taber{
					display: flex;
					flex-wrap: wrap;
					text-align: center;
					justify-content: center;
					text{
						width: 100%;
						font-size: 30rpx;
						font-weight: bold;
					}
					.box{
						width: 35rpx;
						margin-top: 10rpx;
						padding: 4rpx;
						border-radius: 100rpx;
						background-color: #c60127;
					}
				}
			}
			
			.right-icon{
				display: flex;
				.icon{
					margin-left: 10rpx;
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
			background-color: #fff;
			padding-bottom: 20rpx;
			display: flex;
			.tb{
				width: 100%;
				display: flex;
				align-items: center;
				justify-content: center;
				span{
					text-align: center;
					
					font-size: 28rpx;
				}
				image{
					width: 25rpx;
					height: 20rpx;
					margin-left: 10rpx;
				}
			}
		}
		.IncomeExpenses-list{
			background-color: #fff;
			margin-top: 20rpx;
			.listTitle{
				padding:20rpx 30rpx;
				padding-bottom:0rpx ;
				display: flex;
				justify-content: space-between;
				text{
					font-size: 40rpx;
					font-weight: bold;
				}
				.yesr{
					display: flex;
					.span{
						display: flex;
						align-items: self-end;
						font-size: 28rpx;
						font-weight: bold;
						margin-left: 10rpx;
					}
				}
				.text-icon{
					display: flex;
					align-items: center;
					color: #6ca1f0;
					image{
						width: 40rpx;
						height: 40rpx;
					}
				}
			}
			.subTitle{
				padding:0 30rpx;
				font-size: 28rpx;
				margin-top: 20rpx;
			}
			.list{
				margin-top: 20rpx;
				background-color: #fff;
				.li{
					padding: 20rpx;
					display: flex;
					border-bottom: 1px solid #f5f5f5;
					align-content: center;
					image{
						width: 60rpx;
						height: 60rpx;
					}
					.date{
						color: #888;
						display: flex;
						flex-wrap: wrap;
						justify-content: center;
						align-items: center;
						view{
							min-width: 40rpx;
							padding: 20rpx;
							span{
								font-size: 35rpx;
								font-weight: bold;
							}
							p{
								text-align: center;
								width: 100%;
								font-size: 18rpx;
							}
						}
						
					}
					.centent{
						flex: 1;
						background-color: #fff;
						display: flex;
						align-items: center;
						.centent-view{
							width: 100%;
							font-size: 25rpx;
							padding: 10rpx;
							display: flex;
							justify-content: space-between;
							.Left-View{
								span{
									font-size: 28rpx;
									
								}
								p{
									padding-top:10rpx ;
									margin-top: 5rpx;
									color: #888;
								}
							}
							.Right-View{
								text-align: right;
								p{
									font-weight: bold;
									margin-top: 5rpx;
									color:#6f6f6f;
									font-size: 30rpx;
									color: #000;
									text{
										padding-left:10rpx;
									}
								}
								view{
									font-size: 25rpx;
									margin-top: 10rpx;
									color: #888;
								}
								
							}
						}
					}
				}
			}
		}
		.month{
			padding: 20rpx 0;
			background-color: #fff;
			.month-box{
				display: flex;
				align-items: center;
				justify-content: center;
				.box{
					background:url('@/static/Transfer-bg-2.png') ;
					background-size:100% 100%;
					margin: 0 10rpx;
					border-radius: 10rpx;
					box-shadow:  0 0 20rpx 1rpx rgba(0, 0, 0, 0.1);
					padding: 10rpx 60rpx;
					display: flex;
					justify-content: center;
					flex-wrap: wrap;
					text-align: center;
					color: #fff;
					font-weight: bold;
					span{
						width: 100%;
					}
				}
			}
			.SubTitme{
				width: 95%;
				text-align: center;
				border-radius: 10rpx;
				margin: 20rpx auto;
				padding: 10rpx 0;
				font-size: 28rpx;
				background-color:#f2f2f2;
			}
			image{
				margin-top: 20rpx;
				width: 100%;
				height: 300rpx;
			}
		}
		
	}
</style>
