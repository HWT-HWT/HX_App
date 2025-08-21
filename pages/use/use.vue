<template>
	<view class="use All">
		<view class="use-Tab">
			<SearchTabVue 
			:topScollct="TopScroll" 
			:leftIcon="false"
			:rightImage="['../../static/title-2.png','../../static/title-3.png']"
			leftwidth="60rpx"
			leftheight="60rpx"
			rightwidth="60rpx"
			rightheight="60rpx"
			></SearchTabVue>
		</view>
		<view class="use-header" v-if="!account">
			<image src="../../static/use-head-1.png" mode=""></image>
			<span @click="Login">登录/注册</span>
		</view>
		<view class="use-header-login" v-else>
			<image src="../../static/use-head-1.png" mode=""></image>
			<view class="header-login">
				<view class="name">
					<span>你好,吴*斐</span>
					<p>上次登录 07-28 16:22</p>
				</view>
				<view class="icon">
					<span>个人信息</span>
					<image src="../../static/upsdk_payment_right.webp" mode=""></image>
				</view>
			</view>
		</view>
		<view class="use-TitleTab">
			<image class="TitleTab-bg" src="@/static/use-bg-1.png" mode=""></image>
			<view class="TitleTab-list">
				<ListViewVue :list="IndexListViewVue" width="65" height="65" font-size="28rpx" @index='getIndex'></ListViewVue>
			</view>
		</view>
		<view class="use-account" v-if="account">
			<view class="account-title">
				<TItleBoxVue title="我的资产" :icon="false"></TItleBoxVue>
				<image src="../../static/boc_finance_eye_open.png" mode=""></image>
			</view>
			<view class="account-conntent" @click="GoIntellectual">
				<TItleBoxVue title="资产概况" SubTitle="切换图表" textColor="#96b7f0" :icon="true" images="../../static/icon-1.png"></TItleBoxVue>
				<view class="money">
					<p>总资产</p>
					<span>￥33,759.98</span>
					<span class="text">最日收益0.00元</span>
				</view>
				<view class="licai">
					<view class="listView" v-for="(item,index) in licai" :key="index">
						<view class="listView-title">{{item.name}} <image src="@/static/icon-2.png" mode=""></image> </view>
						<p>{{item.subname}}</p>
					</view>
				</view>
				<view class="TShi">
					<image src="@/static/icon-3.png" mode=""></image>
					<p>闲钱随时放,支付随心享 点击查看> </p>
				</view>
			</view>
		</view>
		<view class="use-accout-datatli" v-if="account">
			<TItleBoxVue title="本月收支" :icon="false" ></TItleBoxVue>
			<view class="datali">
				<view class="DataliView">
					<span>收入</span>
					<text>￥0.00</text>
				</view>
				<view class="DataliView" style="text-align: right;">
					<span>收入</span>
					<text>￥0.00</text>
				</view>
				<view class="XT">
					
				</view>
			</view>
		</view>
		<view class="use-myCard AllPage">
			<TItleBoxVue title="我的信用卡" :icon="false"></TItleBoxVue>
			<view class="listView">
				<p>办卡领豪礼</p>
				<span>新户达标享好礼</span>
				<text>立即申请</text>
			</view>
		</view>
		<view class="use-myCard AllPage " v-if="!account">
			<TItleBoxVue title="我的贷款" :icon="false"></TItleBoxVue>
			<view class="listView tow">
				<p>菁英e贷·随借随还</p>
				<span>最高可借500,000元</span>
				<text>立即申请</text>
			</view>
		</view>
		<view class="use-myCard AllPage " @click="Goload" v-else>
			<TItleBoxVue title="我的贷款" :icon="true"></TItleBoxVue>
			<view class="listView tow" style="background:#fff;">
				<span>剩余未还本金 <text style="color: #ccaa7b; border: 1px solid; margin-left: 20rpx; font-size: 20rpx;">个人经营性贷款</text> </span>
				<p>￥365,000.00</p>
			</view>
		</view>
		<view class="use-guarantee AllPage">
			<TItleBoxVue title="我的保障" :icon="false"></TItleBoxVue>
			<view class="use-guaranteeBox">
				<view class="guaranteeListView" v-for="(item,index) in guarantee" :key="index">
					<image :src="item.images" mode=""></image>
					<p>{{item.name}}</p>
					<text>去查询</text>
				</view>
			</view>
			
		</view>
		<view class="use-serve">
			<TItleBoxVue title="我的服务" :icon="false"></TItleBoxVue>
			<view class="serve-box">
				<view class="topic">
					<span style="padding: 0 20rpx; font-size: 35rpx; font-weight: bold;">我的主题</span>
					<image src="../../static/use-topic-1.png" mode=""></image>
				</view>
				
				<view class="safe">
					<TItleBoxVue title="安全中心"></TItleBoxVue>
					<view class="safeList">
						<ListViewVue :list="safe" width="60" height="60" font-size="25rpx" BoxWodth="130rpx"></ListViewVue>
					</view>
				</view>
				
				<view class="Outlets">
					<TItleBoxVue title="周边网点"></TItleBoxVue>
					<view class="Outletslist">
						<p>定位未开启</p>
						<span>开启定位后可 <br /> 获取网点信息</span>
						<text>开启定位</text>
					</view>
				</view>
				
				<view class="Customer">
					<TItleBoxVue title="客服帮助" :icon="false"></TItleBoxVue>
					<view class="Customerlist">
						<view class="Customerbox">
							<view class="textView">
								<p>办理业务帮助</p>
								<span>1对1视频服务</span>
							</view>
							<image src="@/static/Customer-icon-1.png" mode=""></image>
						</view>
						<view class="Customerbox">
							<view class="textView">
								<p>在线客服答疑</p>
								<span>有疑问来问我</span>
							</view>
							<image src="@/static/Customer-icon-2.png" mode=""></image>
						</view>
					</view>
				</view>
				
				<view class="collection">
					<TItleBoxVue title="我的收藏" :icon="false"></TItleBoxVue>
					<image src="@/static/collection-bg-1.png" mode=""></image>
					<p>收藏轻松看</p>
					<span>收藏的理财基金产品在这里</span>
				</view>
				
				<view class="assess">
					<TItleBoxVue title="理财风险评估" :icon="false"></TItleBoxVue>
					<image src="@/static/assess-bg-1.png" mode=""></image>
					<p>查看风险评估</p>
					<span>快来查看风险等吧~</span>
				</view>
			</view>
		</view>
		<view class="use-setting">
			<TItleBoxVue titleSize="35rpx" title="更多服务" :icon="false"></TItleBoxVue>
			<view style="margin-top: 40rpx;"></view>
			<ListViewVue :list="stting" width="65" height="65" font-size="25rpx" @index='index'></ListViewVue>
		</view>
	</view>
</template>

<script>
	import SearchTabVue from '../../components/SearchTab.vue';
	import ListViewVue from '../../components/ListView.vue';
	import TItleBoxVue from '../../components/TItleBox.vue';
	export default {
		data() {
			return {
				TopScroll:0,
				IndexListViewVue:[
					{name:'我的账户',images:'../../static/use-icon-1.png'},
					{name:'收支帐单',images:'../../static/use-icon-2.png'},
					{name:'远程银行',images:'../../static/use-icon-3.png'},
					{name:'我的权益',images:'../../static/use-icon-4.png'},
					{name:'更多',images:'../../static/use-icon-5.png'},
				],
				guarantee:[
					{name:'保险',images:'../../static/use-gu-icon-1.png'},
					{name:'医保',images:'../../static/use-gu-icon-2.png'},
					{name:'社保',images:'../../static/use-gu-icon-3.png'},
				],
				safe:[
					{name:'我的账户',images:'../../static/use-icon-1.png'},
					{name:'收支帐单',images:'../../static/use-icon-2.png'},
					{name:'远程银行',images:'../../static/use-icon-3.png'},
					{name:'我的权益',images:'../../static/use-icon-4.png'},
				],
				stting:[
					{name:'意见反馈',images:'../../static/all-sever-1.png'},
					{name:'关于我们',images:'../../static/all-sever-2.png'},
					{name:'保护政策',images:'../../static/all-sever-3.png'},
					{name:'版本更新',images:'../../static/all-sever-4.png'},
				],
				licai:[
					{name:'存款',subname:'简单一点,存多一点'},
					{name:'理财',subname:'随心放,安心之选'},
					{name:'基金',subname:'10元试试'},
					{name:'信托',subname:'陪伴您的财富成长'},
				],
				account:''
			};
		},
		components:{
			SearchTabVue,
			ListViewVue,
			TItleBoxVue
		},
		onPageScroll(TopScroll) {
			this.TopScroll = TopScroll.scrollTop
		},
		methods:{
			Goload(){
				uni.navigateTo({
					url:'/pages/load/load?id=2'
				})
			},
			Login(){
				uni.navigateTo({
					url:'/pages/gesture/gesture'
				})
			},
			GoIntellectual(){
				uni.navigateTo({
					url:'/pages/Intellectual/Intellectual'
				})
			},
			getIndex(index){
				index == 0 ? uni.navigateTo({
					url:'/pages/account/account'
				})  : '' 
				index == 1 ? uni.navigateTo({
					url:'/pages/IncomeExpenses/IncomeExpenses'
				})  : '' 
			},
			index(index){
				console.log(index);
				index === 3 ? uni.clearStorage('account') :''
				uni.reLaunch({
					url: '/pages/index/index'
				})
			}
		},
		onLoad() {
			this.account = uni.getStorageSync('account').token;
		},
	}
</script>

<style lang="scss">
	.use{
		padding-bottom: 20rpx;
		.use-header{
			display: flex;
			align-items: center;
			image{
				width: 100rpx;
				margin:0 40rpx;
				height: 100rpx;
			}
			span{
				font-weight: bold;
				font-size: 35rpx;
			}
		}
		.use-header-login{
			display: flex;
			align-items: center;
			margin-top: 20rpx;
			image{
				width: 100rpx;
				margin:0 40rpx;
				height: 100rpx;
			}
			.header-login{
				flex: 1;
				display: flex;
				justify-content: space-between;
				.name{
					span{
						font-size: 32rpx;
						font-weight: bold;
					}
					p{
						font-size: 22rpx;
					}
				}
				.icon{
					display: flex;
					justify-content: center;
					align-items: center;
					span{
						font-size: 28rpx;
						margin-right: -35rpx;
					}
					image{
						width: 50rpx;
						height: 50rpx;
					}
				}
			}
			
		}
		.use-TitleTab{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			border-radius:20rpx;
			margin-top: 20rpx;
			.TitleTab-bg{
				width: 100%;
				height: 60rpx;
			}
		}
		.use-account{
			margin-top: 20rpx;
			.account-title{
				display: flex;
				align-items: center;
				image{
					width: 40rpx;
					height: 40rpx;
					margin-left: -10rpx;
				}
			}
			.account-conntent{
				width: 95%;
				margin: 0 auto;
				margin-top: 20rpx;
				background: url('@/static/use-bg-4.png')no-repeat;
				background-size: 100% 100%;
				padding: 20rpx 0;
				.money{
					display: flex;
					flex-wrap: wrap;
					padding: 20rpx;
					font-size: 30rpx;
					span{
						width: 100%;
						margin: 20rpx auto;
						font-size: 45rpx;
						font-weight: bold;
					}
					.text{
						font-size: 28rpx;
						color: #888;
					}
				}
				.licai{
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					.listView{
						width: 40%;
						padding: 20rpx;
						.listView-title{
							align-items: center;
							font-size: 28rpx;
							color: #888;
							image{
								width: 15rpx;
								height: 15rpx;
								margin: 0 10rpx;
							}
						}
						p{
							font-size: 28rpx;
							font-weight: bold;
							margin-top: 10rpx;
						}
					}
				}
				.TShi{
					display: flex;
					align-items: center;
					width: 95%;
					margin: 0 auto;
					background-color: #f5f7fa;
					border-radius: 10rpx;
					padding: 20rpx 0;
					font-size: 26rpx;
					color: #888;
					image{
						margin:0 20rpx;
						width: 13rpx;
						height: 13rpx;
					}
				}
			}
		}
		.use-accout-datatli{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			margin-top: 20rpx;
			padding: 20rpx 0;
			.datali{
				display: flex;
				align-items: center;
				flex-wrap: wrap;
				justify-content: space-between;
				.DataliView{
					width: 100rpx;
					display: flex;
					flex-wrap: wrap;
					margin: 20rpx;
					span{
						width: 100%;
						color: #888;
						font-size: 28rpx;
					}
					text{
						font-weight: bold;
						font-size: 34rpx;
					}
				}
				.XT{
					width: 90%;
					margin: 0 auto;
					padding: 6rpx;
					border-radius: 50rpx;
					margin-top: 10rpx;
					background-color: #a0bdfc;
				}
			}
		}
		.use-myCard{
			.listView{
				padding: 20rpx;
				display: flex;
				flex-wrap: wrap;
				background:url('../../static/use-bg-2.png');
				background-size: 100% 100%;
				line-height: 45rpx;
				p{
					width: 100%;
					font-size: 34rpx;
					font-weight: bold;
				}
				span{
					width: 100%;
					font-size: 25rpx;
					color: #888;
				}
				text{
					color: #9fbde2;
					margin-top: 5rpx;
					font-size: 25rpx;
				}
			}
			.tow{
				background:url('../../static/use-bg-3.png');
				background-size: 100% 100%;
			}
		}
		.use-guarantee{
			.use-guaranteeBox{
				display: flex;
				justify-content: space-evenly;
				margin-top: 20rpx;
				.guaranteeListView{
					display: flex;
					justify-content: center;
					flex-wrap:wrap;
					text-align: center;
					margin: 20rpx;
					image{
						width: 65rpx;
						height: 65rpx;
					}
					p{
						margin-top: 5rpx;
						font-size: 25rpx;
						width: 100%;
					}
					text{
						margin-top: 10rpx;
						font-size: 25rpx;
						width: 100%;
						color: #98b7e4;
					}
				}
			}
		}
		.use-serve{
			margin: 20rpx 0;
			.serve-box{
				width: 100%;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-evenly;
				margin: 20rpx 0;
				.topic{
					width: 46%;
					background-color: #fff;
					border-radius: 20rpx;
					padding-top: 20rpx;
					image{
						width: 90%;
						height: 300rpx;
						margin:20rpx;
					}
				}
				.safe{
					width: 46%;
					background-color: #fff;
					border-radius: 20rpx;
					padding-top: 20rpx;
					.safeList{
						background-color: #f6f7fb;
						width: 90%;
						margin: 0 auto;
						margin-top: 20rpx;
						display: flex;
						align-items: center;
						border-radius: 20rpx;
					}
				}
				.Outlets{
					width: 46%;
					background-color: #fff;
					border-radius: 20rpx;
					padding-top: 20rpx;
					margin-top: 20rpx;
					background:url('../../static/Outlets-bg-1.png') ;
					background-size: 100% 100%;
					.Outletslist{
						padding: 20rpx ;
						display: flex;
						flex-wrap: wrap;
						line-height: 45rpx;
						p{
							font-weight: bold;
							font-size: 30rpx;
						}
						span{
							width: 100%;
							font-size: 25rpx;
							color:#888;
						}
						text{
							color:#9ebfef;
							font-size: 28rpx;
							margin-top: 40rpx;
							padding: 20rpx 0;
						}
					}
				}
				.Customer{
					width: 46%;
					background-color: #fff;
					border-radius: 20rpx;
					padding-top: 20rpx;
					margin-top: 20rpx;
					.Customerlist{
						width: 90%;
						margin: 20rpx auto;
						.Customerbox{
							border-radius: 20rpx;
							background-color: #f6f7fb;
							padding-bottom: 20rpx;
							margin-top: 20rpx;
							display: flex;
							align-items: center;
							justify-content: space-between;
							padding: 20rpx;
							p{
								
								font-weight: bold;
								font-size: 30rpx;
							}
							span{
								color: #888;
								font-size: 25rpx
							}
							image{
								width: 60rpx;
								height: 60rpx;
							}
						}
						
					}
				}
				.collection{
					width: 46%;
					background-color: #fff;
					border-radius: 20rpx;
					padding: 20rpx 0;
					margin-top: 20rpx;
					image{
						width: 100rpx;
						height: 80rpx;
						margin:0 20rpx;
						margin-top: 80rpx;
					}
					p{
						padding: 20rpx;
						font-weight: bold;
						font-size: 30rpx;
					}
					span{
						padding:0 20rpx;
						color: #888;
						font-size: 22rpx
					}
				}
				.assess{
					width: 46%;
					background-color: #fff;
					border-radius: 20rpx;
					padding: 20rpx 0;
					margin-top: 20rpx;
					image{
						width: 100rpx;
						height: 100rpx;
						margin:0 20rpx;
						margin-top: 60rpx;
					}
					p{
						color: #6e9cde;
						padding: 20rpx;
						font-weight: bold;
						font-size: 30rpx;
					}
					span{
						padding:0 20rpx;
						color: #888;
						font-size: 22rpx
					}
				}
			}
			
		}
		.use-setting{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background: #fff;
			border-radius: 20rpx;
			padding: 20rpx 0;
		}
	}
</style>
