<template>
	<view class="index">
		<view class="index-Tab">
			<SearchTabVue :topScollct="TopScroll"></SearchTabVue>
		</view>
		<view class="index-TitleTab">
			<image class="TitleTab-bg" src="@/static/index-TitleTab-1.png" mode=""></image>
			<view class="TitleTab-list">
				<ListViewVue :list="IndexListViewVue" width="80" height="80" font-size="30rpx" @index='GetIndex'></ListViewVue>
			</view>
		</view>
		<view class="index-logoinView" v-if="!account">
			<view class="TextView">
				<span>Hello,上午好!</span>
				<text>登录后可查看账户余额</text>
			</view>
			<view class="Btn" @click="Login">
				去登陆
			</view>
		</view>
		<view class="index-DoLogoin" v-else>
			<view class="TextView">
				<view @click="eye">
					可用余额 
					<image src="../../static/boc_finance_eye_close.png" mode="" v-if="TrueEye"></image> 
					<image src="../../static/boc_finance_eye_open.png" mode="" v-else></image>
				</view>
				<span>华夏卡</span>
			</view>
			<text v-if="TrueEye">******</text>
			<text v-else>33,759.98</text>
			<p>美元个人结构性存款,2000美元起存,点击...</p>
		</view>
		<view class="index-listview">
			<ListViewVue :list="ListView" width="65" height="65" font-size="28rpx" @index="getListIindex"></ListViewVue>
		</view>
		<view class="index-advertisement">
			<view class="advertisement-ListView">
				<view class="ListView-image">
					<view class="ListTitle">
						<image src="@/static/advertisement-logo-1.png" mode=""></image>
						公告
					</view>
					华夏银行系统升级公告
				</view>
				<view class="ListView-image">
					<view class="ListTitle">
						<image src="@/static/advertisement-logo-1.png" mode=""></image>
						公告
					</view>
					防范非金融活动,守护自身...
				</view>
			</view>
			<view class="message">
				<image src="@/static/advertisement-2.png" mode=""></image>
				<span>消息</span>
			</view>
		</view>
		<view class="index-Money">
			<investTextBoxVue :list="TextBox"></investTextBoxVue>
		</view>
		<view class="index-Money">
			<TItleBoxVue title="财富精选" SubTitle="更多"></TItleBoxVue>
			<view class="Money">
				<investTextBoxVue :list="TextBoxs" :btn='true'></investTextBoxVue>
			</view>
			<view class="SubMoney">
				<view class="SubMoney-view">
					<p>1元起购</p>
					<span>5.12%</span>
					<text>成立以来年化</text>
				</view>
				<view class="SubMoney-view">
					<p>1元起购</p>
					<span>5.12%</span>
					<text>成立以来年化</text>
				</view>
				<view class="SubMoney-view">
					<p>1元起购</p>
					<span>5.12%</span>
					<text>成立以来年化</text>
				</view>
			</view>
		</view>
		<view class="index-banner">
			<bannerImageVue :images='banner'></bannerImageVue>
		</view>
		<view class="index-hot">
			<TItleBoxVue title="热门活动" SubTitle="更多"></TItleBoxVue>
			<view class="MixBanner">
				<p>积分权益商城</p>
				<span>能量驿站 给生活加满能量</span>
			</view>
			<view class="MinBanner">
				<view class="MixBanner">
					<p>每天能量雨</p>
					<span>大美华夏旅游季</span>
				</view>
				<view class="MixBanner Tow">
					<p>元气“薪”期三</p>
					<span>抽好礼 半价兑</span>
				</view>
			</view>
		</view>
		<view class="index-loan">
			<TItleBoxVue title="借钱服务" SubTitle="更多"></TItleBoxVue>
			<view class="loan-view">
				<view class="title">
					<p>50万</p>
					<span>最高可贷(元)</span>
				</view>
				<view class="title ">
					<p class="black">龙e贷</p>
					<span>纯信用贷款 | 年华利率低至3.5%</span>
				</view>
				<image src="../../static/dis_renwu_next.png" mode=""></image>
			</view>
			
			<view class="loan-view Tow">
				<view class="title">
					<p>500万</p>
					<span>最高可贷(元)</span>
				</view>
				<view class="title ">
					<p class="black">龙商贷</p>
					<span>纯信用贷款 | 随借随用</span>
				</view>
				<image src="../../static/dis_renwu_next.png" mode=""></image>
			</view>
			
		</view>
		<view class="index-cardZooz">
			<TItleBoxVue title="信用卡专区" SubTitle="更多"></TItleBoxVue>
				<view class="swiperView">
					<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
						<swiper-item>
							<image src="@/static/index-banner-image-6.png" mode=""></image>
						</swiper-item>
						<swiper-item>
							<image src="@/static/index-banner-image-6.png" mode=""></image>
						</swiper-item>
					</swiper>
					<view class="banner">
						<view class="MixBanner">
							<p>办卡领豪礼</p>
							<span>新户达标享好礼</span>
							
						</view>
						<view class="banner-box">
							<ListViewVue :list="cardzooz" width="60" height="60" font-size="25rpx" BoxWodth="150rpx"></ListViewVue>
						</view>
						
					</view>
				</view>
		</view>
		<view class="index-load">
			<image class="TitleTab-bg" src="@/static/index-load-1.png" mode=""></image>
			<view class="TitleTab-list">
				<view class="list-image">
					<image src="../../static/index-load-2.png" mode=""></image>
					<view class="TextView">
						<p>安全守护</p>
						<span>守护资金安全</span>
					</view>
				</view>
				<view class="list-image">
					<image src="../../static/index-load-3.png" mode=""></image>
					<view class="TextView">
						<p>打字版</p>
						<span>使用更简单</span>
					</view>
				</view>
			</view>
		</view>
		<view class="index-Phone">
			<TItleBoxVue title="您对新版手机银行感到满意吗?" :icon="false"></TItleBoxVue>
			<view class="listview">
				<ListViewVue :list="phone" width="80" height="75" font-size="25rpx" BoxWodth="15%" textColor="#888"></ListViewVue>
			</view>
		</view>
		<view class="index-PhoneNumber">
			<view class="Number">
				<input type="text" placeholder="请输入充值号码"/>
				<span>通讯录 <image src="../../static/dis_renwu_next.png" mode=""></image> </span>
			</view>
			<view class="Money">
				<view class="btn">
					100元
				</view>
				<view class="btn">
					200元
				</view>
				<view class="btn">
					300元
				</view>
			</view>
		</view>
		<view class="index-Bug">
			<TItleBoxVue title="遇到问题" :icon="false"></TItleBoxVue>
			<view class="MinBanner">
				<view class="MixBanner">
					<p>安全中心</p>
					<span>实时保护</span>
				</view>
				<view class="MixBanner Tow">
					<p>远程银行</p>
					<span>足不出户</span>
				</view>
				<view class="MixBanner three">
					<p>投诉渠道</p>
					<span>多种渠道</span>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import SearchTabVue from '@/components/SearchTab.vue'
	import ListViewVue from '../../components/ListView.vue'
	import investTextBoxVue from '../../components/invest-textBox.vue'
	import TItleBoxVue from '../../components/TItleBox.vue'
	import bannerImageVue from '../../components/banner-image.vue'
	export default {
		data() {
			return {
				IndexListViewVue:[
					{name:'贷款',images:'../../static/index-listView-4.png'},
					{name:'理财',images:'../../static/index-listView-1.png'},
					{name:'转账',images:'../../static/index-listView-2.png'},
					{name:'我的账户',images:'../../static/index-listView-3.png'},
					
				],
				ListView:[
					{name:'存款',images:'../../static/index-icon-1.png'},
					{name:'每日签到',images:'../../static/index-icon-2.png'},
					{name:'收支账单',images:'../../static/index-icon-3.png'},
					{name:'养老金融',images:'../../static/index-icon-4.png'},
					{name:'惠加油',images:'../../static/index-icon-5.png'},
					{name:'安全中心',images:'../../static/index-icon-6.png'},
					{name:'理财',images:'../../static/index-icon-7.png'},
					{name:'贷款',images:'../../static/index-icon-8.png'},
					{name:'基金',images:'../../static/index-icon-9.png'},
					{name:'更多',images:'../../static/index-icon-10.png'},
				],
				TextBox:{
					border:false,
					title:'稳健存款',
					Subtitle:'惠盈2303号三层看涨AU9999(贵宾专属)',
					leftTop:'0.85/1.12/2.32%',
					leftBottom:'逾期年化收益率..',
					rigthTop:'86天/30万元起存',
					rigthBottom:['存款期限','起存金额'],
					tisiFooter:'*关联货币基金七日年化分布在1.1970%-2.3190%'
				},
				TextBoxs:{
					border:false,
					Subtitle:'华夏理财固收纯债最短持有7天X款A',
					leftTop:'3.93%',
					leftBottom:'成立以来年化',
					rigthTop:'持有七天后可赎',
					rigthBottom:['R2中低风险','1元起购'],
					tisiFooter:'*关联货币基金七日年化分布在1.1970%-2.3190%'
				},
				banner:['../../static/index-banner-image-1.png','../../static/index-banner-image-2.png','../../static/index-banner-image-3.png','../../static/index-banner-image-4.png','../../static/index-banner-image-5.png'],
				cardzooz:[
					{name:'办卡进度',images:'../../static/index-cardzooz-icon-1.png'},
					{name:'开卡激活',images:'../../static/index-cardzooz-icon-2.png'},
					{name:'添加卡片',images:'../../static/index-cardzooz-icon-3.png'},
					{name:'查账还款',images:'../../static/index-cardzooz-icon-4.png'},
				],
				phone:[
					{name:'非常不满',images:'../../static/face-1.png'},
					{name:'太不满意',images:'../../static/face-2.png'},
					{name:'一般',images:'../../static/face-3.png'},
					{name:'笔记满意',images:'../../static/face-4.png'},
					{name:'非常满意',images:'../../static/face-5.png'},
				],
				TopScroll:0,
				TrueEye:true,
				account:''
			}
		},
		methods: {
			Login(){
				uni.navigateTo({
					url:'/pages/gesture/gesture'
				})
			},
			eye(){
				this.TrueEye = !this.TrueEye
			},
			GetIndex(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/load/load'
				}) : ''
				// console.log(index);
				index === 2 ? uni.navigateTo({
					url:'/pages/TransferPage/TransferPage'
				}) : ''
				index === 3 ? uni.navigateTo({
					url:'/pages/account/account'
				}) : ''
			},
			getListIindex(index){
				index === 2 ? uni.navigateTo({
					url:'/pages/IncomeExpenses/IncomeExpenses'
				}) : ''
			}
		},
		onLoad(account) {
			this.account = uni.getStorageSync('account').token;
		},
		components:{
			SearchTabVue,
			ListViewVue,
			investTextBoxVue,
			TItleBoxVue,
			bannerImageVue
		},
		onPageScroll(Scroll) {
			this.TopScroll = Scroll.scrollTop
		}
	}
</script>

<style lang="scss" scoped>
	.index{
		width: 100vw;
		min-height: 100vh;
		padding-bottom: 50rpx;
		background-color: #f6f7fb;
		.index-TitleTab{
			width: 90%;
			margin: 0 auto;
			background-color: #fff;
			border-radius:20rpx;
			.TitleTab-bg{
				width: 100%;
				height: 200rpx;
			}
		}
		.index-logoinView{
			width: 90%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			margin-top: 20rpx;
			border-radius: 20rpx;
			background-color: #fff;
			.TextView{
				flex: 1;
				display: flex;
				flex-wrap: wrap;
				padding: 20rpx;
				span{
					width: 100%;
					font-size: 35rpx;
					font-weight: bold;
				}
				text{
					margin-top: 10rpx;
					font-size: 28rpx;
				}
			}
			.Btn{
				border: 1px solid;
				padding:10rpx 20rpx;
				font-size: 30rpx;
				margin: 0 30rpx;
				color: #fff;
				background-color: #db0f1b;
				border-radius: 50rpx;
			}
		}
		.index-DoLogoin{
			width: 85%;
			margin: 0 auto;
			padding: 20rpx;
			background-color: #fff;
			border-radius: 20rpx;
			margin-top: 20rpx;
			.TextView{
				display: flex;
				justify-content: space-between;
				font-size: 28rpx;
				margin-bottom: 20rpx;
				font-weight: bold;
				align-items: center;
				view{
					display: flex;
					image{
						width: 40rpx;
						height: 40rpx;
						margin: 0 10rpx;
					}
				}
				
			}
			text{
				font-size: 45rpx;
			}
			p{
				font-size: 25rpx;
				margin-top: 20rpx;
				color: #e28f41;
			}
		}
		.index-listview{
			width: 90%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
		.index-advertisement{
			width: 90%;
			margin: 0 auto;
			display: flex;
			align-items: center;
			justify-content: space-between;
			background-color: #fff;
			border-radius: 20rpx;
			.advertisement-ListView{
				.ListView-image{
					display: flex;
					line-height: 45rpx;
					font-size: 28rpx;
					.ListTitle{
						font-size: 28rpx;
						display: flex;
						align-items: center;
						font-weight: bold;
						padding: 0 10rpx;
						image{
							margin:0 10rpx;
							width: 35rpx;
							height: 35rpx;
						}
					}
				}
			}
			.message{
				display: flex;
				flex-wrap: wrap;
				justify-content: center;
				margin:0 20rpx;
				padding:10rpx 20rpx;
				font-size: 28rpx;
				text-align: center;
				image{
					width: 60rpx;
					height: 60rpx;
				}
				span{
					width: 100%;
					font-size: 28rpx;
				}
			}
		}
		.index-Money{
			width: 90%;
			margin: 0 auto;
			border-radius: 20rpx;
			padding: 20rpx;
			margin-top: 20rpx;
			background-color: #fff;
			.SubMoney{
				display: flex;
				.SubMoney-view{
					flex: 1;
					background-color: #f6f7fb;
					padding: 20rpx;
					border-radius: 20rpx;
					margin: 0 15rpx;
					display: flex;
					flex-wrap: wrap;
					text-align: center;
					justify-content: center;
					p{
						font-size: 25rpx;
						font-weight: bold;
					}
					span{
						width: 100%;
						padding: 10rpx 0;
						font-size: 30rpx;
						color: #c91d29;
						font-weight: bold;
					}
					text{
						font-size: 20rpx;
						color:#888;
					}
				}
			}
			.MaxImage{
				width: 95%;
				padding:0 20rpx;
				height: 180rpx;
				margin-top: 10rpx;
			}
			.MinImage{
				width: 95%;
				margin: 0 auto;
				display: flex;
				justify-content: space-between;
				image{
					width: 49%;
					height: 180rpx;
					margin-top: 5rpx;
				}
			}
		}
		.index-hot{
			width: 90%;
			margin: 0 auto;
			border-radius: 20rpx;
			padding: 20rpx;
			margin-top: 20rpx;
			background-color: #fff;
			.MixBanner{
				background: url('../../static/index-hot-3.png');
				background-size:100% 100%;
				padding: 20rpx;
				line-height: 45rpx;
				padding-bottom: 60rpx;
				border-radius: 20rpx;
				margin-top: 20rpx;
				font-size: 30rpx;
				display: flex;
				flex-wrap: wrap;
				p{
					width: 100%;
					margin-top: 20rpx;
					font-weight: bold;
				}
				span{
					font-size: 26rpx;
					color: #888;
				}
			}
			.MinBanner{
				display: flex;
				justify-content: space-between;
				.MixBanner{
					width: 43%;
					padding: 20rpx;
					background-color: #f6f7fb;
					padding-bottom:60rpx;
					background: url('../../static/index-hot-1.png');
					background-size:100% 100% ;
				}
				.Tow{
					background: url('../../static/index-hot-2.png');
					background-size:100% 100% ;
				}
			}
		}
		.index-loan{
			width: 90%;
			margin: 0 auto;
			border-radius: 20rpx;
			padding: 20rpx;
			margin-top: 20rpx;
			background-color: #fff;
			.loan-view{
				background: url('../../static/index-loan-1.png');
				background-size:100% 100%;
				border-radius: 20rpx;
				margin-top: 20rpx;
				align-items: center;
				display: flex;
				padding: 40rpx 20rpx;
				justify-content: space-between;
				.title{
					flex: 1;
					p{
						font-size: 35rpx;
						font-weight: bold;
						color: #cc1c26;
					}
					span{
						color: #333;
						font-size: 22rpx;
					}
					.black{
						color: #000;
					}
				}
				image{
					width: 22rpx;
					height: 22rpx;
					margin: 10rpx;
				}
			}
			.Tow{
				background: url('../../static/index-loan-2.png');
				background-size:100% 100%;
			}
		}
		.index-cardZooz{
			width: 95%;
			margin: 0 auto;
			border-radius: 20rpx;
			padding: 20rpx 0;
			margin-top: 20rpx;
			background-color: #fff;
			.swiperView{
				padding: 20rpx;
				margin-top: 20rpx;
				display: flex;
				justify-content: space-between;
				border-radius: 20rpx;
				swiper{
					width: 49%;
					height: 500rpx;
					::v-deep.uni-swiper-dot{
						width: 10rpx;
						height: 10rpx;
						border-radius: 0;
						background-color: #ad8e85;
					}
					::v-deep.uni-swiper-dot-active{
						width: 10rpx;
						height: 10rpx;
						border-radius: 0;
						background-color: #000;
					}
					image{
						width: 100%;
						height: 100%;
						border-radius: 20rpx;
					}
				}
				.banner{
					width: 49%;
					.MixBanner{
						padding:30rpx;
						padding-bottom: 90rpx;
						background-color: #f6f7fb;
						background: url('../../static/index-cardzooz-1.png');
						background-size:100% 100%;
						p{
							width: 100%;
							font-weight: bold;
						}
						span{
							font-size: 26rpx;
							color: #888;
						}
					}
					.banner-box{
						margin-top: 10rpx;
						padding: 5rpx;
						border-radius: 20rpx;
						background-color: #f6f7fb;
					}
				}
			}
			
		}
		.index-load{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			border-radius:20rpx;
			.TitleTab-bg{
				width: 100%;
				height: 170rpx;
			}
			.TitleTab-list{
				margin-top: -10rpx;
				display: flex;
				justify-content: space-evenly;
				background-color: #fff;
				.list-image{
					align-items: center;
					display: flex;
					image{
						margin: 20rpx;
						width: 80rpx;
						height: 80rpx;
					}
					.TextView{
						font-size: 30rpx;
						padding: 20rpx;
						p{
							font-weight: bold;
						}
						span{
							font-size: 25rpx;
							color: #888;
						}
					}
					
				}
			}
		}
		.index-Phone{
			width: 95%;
			background-color: #fefefe;
			margin: 0 auto;
			margin-top: 20rpx;
			padding: 20rpx 0;
			border-radius:20rpx;
			background-color: #fff;
			.listview{
				margin-top: 20rpx;
			}
		}
		.index-PhoneNumber{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			margin-top: 20rpx;
			border-radius: 20rpx;
			padding-bottom: 20rpx;
			input{
				font-size: 30rpx;
			}
			.Number{
				padding: 30rpx;
				display: flex;
				align-items: center;
				justify-content: space-between;
				span{
					font-size: 25rpx;
					image{
						width: 20rpx;
						height: 20rpx;
					}
				}
			}
			.Money{
				display: flex;
				justify-content: space-evenly;
				
				.btn{
					font-weight: bold;
					padding: 10rpx 60rpx;
					border-radius: 10rpx;
					background-color: #f6f7fb;
				}
			}
		}
		.index-Bug{
			width: 95%;
			background-color: #fefefe;
			margin: 0 auto;
			margin-top: 20rpx;
			padding: 20rpx 0;
			border-radius:20rpx;
			background-color: #fff;
			.MinBanner{
				display: flex;
				justify-content: space-evenly;
				.MixBanner{
					width: 25%;
					margin-top: 20rpx;
					padding: 20rpx;
					background-color: #f6f7fb;
					padding-bottom:60rpx;
					background: url('../../static/bug-1.png');
					background-size:100% 100% ;
					p{
						font-size: 28rpx;
						font-weight: bold;
					}
					span{
						font-size: 25rpx;
						color: #888;
					}
				}
				.Tow{
					background: url('../../static/bug-2.png');
					background-size:100% 100% ;
				}
				.three{
					background: url('../../static/bug-3.png');
					background-size:100% 100% ;
				}
			}
		}
	}
</style>
