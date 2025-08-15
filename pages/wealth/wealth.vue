<template>
	<view class="wealth">
		<view class="wealth-Tab">
			<SearchTabVue 
			:topScollct="TopScroll" 
			leftImage="../../static/title-1.png" 
			:rightImage="['../../static/title-2.png','../../static/title-3.png']"
			leftwidth="60rpx"
			leftheight="60rpx"
			rightwidth="60rpx"
			rightheight="60rpx"
			></SearchTabVue>
		</view>
		<view class="wealth-assets">
			<view class="assets">
				<view class="p">我的总资产 <image src="../../static/wealth-icon-1.png" mode=""></image> </view>
				<view class="span">登陆后查看资产 <image src="../../static/dis_renwu_next.png" mode=""></image> </view>
			</view>
			<view class="assets">
				<view class="p">昨日收益 <image src="../../static/wealth-icon-1.png" mode=""></image> </view>
				<view class="span">****** <image src="../../static/dis_renwu_next.png" mode=""></image> </view>
			</view>
		</view>
		<view class="wealth-listview">
			<ListViewVue :list="ListView" width="65" height="65" font-size="28rpx"></ListViewVue>
		</view>
		<view class="wealth-collection">
			<TItleBoxVue titleSize="30rpx"  title="我的收藏" SubTitle="收藏轻松看"></TItleBoxVue>
		</view>
		<view class="wealth-swiper">
			<swiper class="leftSwiper" :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
				<swiper-item>
					<view class="swiperView">
						<p>活钱宝 焕然升级</p>
						<span>打造一站式活钱管理专区</span>
						<view class="btn">
							去体验
						</view>
					</view>
				</swiper-item>
			</swiper>
			
			<view class="rightSwiper">
				<swiper 
				:indicator-dots="true" 
				:autoplay="true" 
				:interval="3000" 
				:duration="1000"
				>
					<swiper-item class="one">
						<view class="swiperView">
							<p>理财PK <text>帮你选出中意的</text> </p>
							<span>选产品对比</span>
						</view>
					</swiper-item>
				</swiper>
				
				<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
					<swiper-item class="tow">
						<view class="swiperView">
							<p>理财榜单</p>
							<span>跟着榜单好上车 <image src="../../static/dis_renwu_next.png" mode=""></image> </span>
						</view>
					</swiper-item>
				</swiper>
			</view>
		</view>
		<view class="wealth-list">
			<view class="NavBtn">
				<view class="Btn" v-for="(item,index) in NavBtn" :key="index" :style="{fontWeight: index == 0 ? 'bold' : 'normal'}">
					{{item}}
				</view>
			</view>
			<view class="image">
				<image src="../../static/wealth-Nav-title-2.png" mode=""></image>
			</view>
			<view class="loan-view">
				<view class="title">
					<span>日日盈</span>
					<p class="black">快捷转账支付</p>
				</view>
				<view class="title ">
					<span>天添宝</span>
					<p class="black">最高取60万</p>
				</view>
			</view>
			<view class="loan-view">
				<view class="title">
					<p>1.38%</p>
					<span style="color: #999;">最高七日年化</span>
					
				</view>
				<view class="title ">
					<p>1.8220%</p>
					<span style="color: #999;">最高七日年化</span>
				</view>
			</view>

		</view>
		<view class="wealth-plan">
			<TItleBoxVue titleSize="35rpx" title="财富规划" SubTitle="更多"></TItleBoxVue>
			<view class="tbs">
				<z-tabs :list="workTaber" :bar-style="{'background' : 'none'}" :tabs-style="{'background':'none',fontWeight: 'bold'}" :active-color='"#000"' bar-width='20rpx' bar-height='10rpx'></z-tabs>
			</view>
			<investTextBoxVue :list='TextBoxone'></investTextBoxVue>
			<investTextBoxVue :list='TextBoxtow'></investTextBoxVue>
			<investTextBoxVue :list='TextBoxthree'></investTextBoxVue>
		</view>
		<view class="wealth-load">
			<TItleBoxVue titleSize="35rpx" title="颐养计划" SubTitle="更多"></TItleBoxVue>
			<view class="loadView">
				<image src="../../static/wealth-load-bg-1.png" mode=""></image>
				<view class="loadicon">
					<ListViewVue :list="load" width="50" height="50" font-size="25rpx"></ListViewVue>
				</view>
			</view>
		</view>
		<view class="wealth-knowledge">
			<TItleBoxVue titleSize="35rpx" title="理财涨知识" SubTitle="更多"></TItleBoxVue>
			<view class="knowledgeView">
				<view class="TextView">
					<text>顶级的自律是什么?</text>
					<span>理财小剧场 2024-11-04</span>
				</view>
				<image src='../../static/bug-1.png' mode=""></image>
			</view>
			<view class="knowledgeView">
				<view class="TextView">
					<text>理财产品到期后资金需要多久天?</text>
					<span>理财基础课 2024-11-04</span>
				</view>
				<image src='../../static/bug-1.png' mode=""></image>
			</view>
		</view>
		<view class="wealth-setting">
			<TItleBoxVue titleSize="35rpx" title="金融工具箱" :icon="false"></TItleBoxVue>
			<ListViewVue :list="stting" width="65" height="65" font-size="25rpx"></ListViewVue>
		</view>
	</view>
</template>

<script>
	import SearchTabVue from '../../components/SearchTab.vue';
	import ListViewVue from '../../components/ListView.vue';
	import TItleBoxVue from '../../components/TItleBox.vue';
	import investTextBoxVue from '../../components/invest-textBox.vue';
	export default {
		data() {
			return {
				TopScroll:0,
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
				NavBtn:['灵活精选','特色多宝','稳优系列','首发精选'],
				workTaber:['活钱稳健','进取投资','保险保障'],
				TextBoxone:{
					title:'华夏理财现金管理理财产品82号B',
					leftTop:'1.2020%',
					leftBottom:'7日年化',
					rigthTop:'交易日申赎·快赎1万元',
					rigthBottom:['R1低风险','1元起购'],
					tisiFooter:'*关联货币基金七日年化分布在1.1970%-2.3190%',
				},
				TextBoxtow:{
					title:'华夏理财固收纯债短持有28天B款A',
					leftTop:'2.40%',
					leftBottom:'成立以来年化',
					rigthTop:'持有28天后可赎',
					rigthBottom:['R2低风险','1元起购'],
					tisiFooter:'*关联货币基金七日年化分布在1.1970%-2.3190%',
					tisiText:'理财产品过往业绩不代表其未来表现，不等于理财产品实际收益.',
				},
				TextBoxthree:{
					title:'华夏理财固收纯债短持有28天B款A',
					leftTop:'2.63%',
					leftBottom:'成立以来年化',
					rigthTop:'交易日申赎',
					rigthBottom:['R2中低风险','1元起购'],
					tisiFooter:'*关联货币基金七日年化分布在1.1970%-2.3190%',
					tisiText:'理财产品过往业绩不代表其未来表现，不等于理财产品实际收益.',
				},
				load:[
					{name:'开户有礼',images:'../../static/wealth-load-icon-1.png'},
					{name:'养老金缴存',images:'../../static/wealth-load-icon-2.png'},
					{name:'我的养老金',images:'../../static/wealth-load-icon-3.png'},
					{name:'缴存记录',images:'../../static/wealth-load-icon-4.png'},
				],
				stting:[
					{name:'销售人员公示',images:'../../static/index-icon-1.png'},
					{name:'合格投资者认证',images:'../../static/index-icon-2.png'},
					{name:'资金归集',images:'../../static/index-icon-3.png'},
					{name:'产品信息查询',images:'../../static/index-icon-4.png'},
				],
		};
		},
		components:{
			SearchTabVue,
			ListViewVue,
			TItleBoxVue,
			investTextBoxVue
		},
		onPageScroll(Scroll) {
			this.TopScroll = Scroll.scrollTop
		}
	}
</script>

<style lang="scss" scoped>
	.wealth{
		width: 100vw;
		min-height: 100vh;
		background:url('../../static/wealth-bg-1.png') no-repeat;
		background-size:100% 350rpx;
		padding-bottom:50rpx;
		background-color: #f6f7fb;
		.wealth-assets{
			display: flex;
			justify-content: space-between;
			padding: 30rpx;
			line-height: 55rpx;
			z-index: 998;
			.assets{
				.p{
					display: flex;
					align-items: center;
					font-size: 28rpx;
					image{
						width: 30rpx;
						height: 30rpx;
						margin: 10rpx;
					}
				}
				.span{
					display: flex;
					align-items: center;
					font-size: 35rpx;
					font-weight: bold;
					image{
						width: 25rpx;
						height: 25rpx;
						margin: 10rpx;
					}
				}
			}
		}
		.wealth-listview{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
		}
		.wealth-collection{
			width: 95%;
			margin: 0 auto;
			background-color: #fff;
			padding: 20rpx 0;
			margin-top:20rpx;
			border-radius: 15rpx;
		}
		.wealth-swiper{
			width: 95%;
			height: 400rpx;
			margin: 0 auto;
			margin-top: 20rpx;
			display: flex;
			justify-content: space-between;
			padding-bottom: 50rpx;
			border-radius: 20rpx;
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
			.leftSwiper{
				padding: 10rpx;
				width: 50%;
				height: 100%;
				swiper-item{
					background:url('../../static/wealth-bg-2.png');
					background-size:100% 100%;
					border-radius: 20rpx;
					.swiperView{
						display: flex;
						flex-wrap: wrap;
						line-height: 50rpx;
						padding: 20rpx;
						p{
							font-size: 34rpx;
							font-weight: bold;
						}
						span{
							font-size: 25rpx;
						}
						.btn{
							padding: 10rpx 35rpx;
							background-color:#de0f1f;
							color: #fff;
							border-radius: 50rpx;
						}
					}
				}
			}
			.rightSwiper{
				padding: 10rpx;
				width: 50%;
				height: 100%;
				border-radius: 20rpx;
				.one{
					background:url('../../static/wealth-bg-3.png');
					background-size:100% 100%;
				}
				.tow{
					background:url('../../static/wealth-bg-4.png');
					background-size:100% 100%;
				}
				swiper{
					height: 50%;
					width: 100%;
					border-radius: 20rpx;
					margin-bottom: 10rpx;
					.swiperView{
						border-radius: 20rpx;
						display: flex;
						flex-wrap: wrap;
						line-height: 50rpx;
						padding: 20rpx;
						p{
							width: 100%;
							font-size: 34rpx;
							font-weight: bold;
							text{
								font-size:25rpx;
								font-weight: normal;
								margin: 10rpx;
								color: #888;
							}
						}
						span{
							font-size: 25rpx;
							image{
								width: 20rpx;
								height: 20rpx;
							}
						}
					}
				}
			}
		}
		.wealth-list{
			width: 95%;
			background-color: #fff;
			border-radius: 20rpx;
			margin: 0 auto;
			.NavBtn{
				padding: 30rpx 0;
				display: flex;
				justify-content: space-evenly;
				background: url('../../static/wealth-Nav-title-1.png');
				background-size: 105% 100%;
			}
			.image{
				width: 95%;
				margin: 0 auto;
				display: flex;
				justify-content: center;
				margin-top: 20rpx;
				image{
					width: 300rpx;
					height: 40rpx;
				}
			}
			.loan-view{
				background-size:100% 100%;
				border-radius: 20rpx;
				align-items: center;
				display: flex;
				padding: 20rpx;
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
						font-size: 30rpx;
					}
				}
			}
		}
		.wealth-plan{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			border-radius: 20rpx;
			padding: 20rpx 0;
			.tbs{
				margin-top: 20rpx;
			}
		}
		.wealth-load{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			padding: 20rpx 0;
			border-radius: 20rpx;
			.loadView{
				border-radius: 20rpx;
				image{
					width: 95%;
					height: 180rpx;
				}
				.loadicon{
					width: 93%;
					border-radius:0 0 20rpx 20rpx;
					margin-top: -10rpx;
					margin-left: 10rpx;
					background: #f5f6fa;
				}
			}
		}
		.wealth-knowledge{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background-color: #fff;
			border-radius: 20rpx;
			padding: 20rpx 0;
			.knowledgeView{
				display: flex;
				justify-content: space-between;
				padding: 30rpx;
				.TextView{
					display: flex;
					flex-wrap: wrap;
					text{
						width: 100%;
						margin-bottom: 20rpx;
						font-weight: bold;
						font-size: 30rpx;
					}
					span{
						margin-top: 20rpx;
						font-size: 20rpx;
						color: #999;
					}
				}
				image{
					width: 100rpx;
					height: 100rpx;
				}
			}
		}
		.wealth-setting{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			background: #fff;
			border-radius: 20rpx;
			padding: 20rpx 0;
		}
	}
</style>
