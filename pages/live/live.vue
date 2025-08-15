<template>
	<view class="live">
		<view class="live-Tab">
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
		<view class="live-listView">
			<view class="listView" v-for="(item,index) in listview" :key="index">
				<image :src="item.images" mode=""></image>
				<view class="TextView">
					<p>{{item.name}}</p>
					<span>{{item.subtitle}}</span>
				</view>
			</view>
		</view>
		<view class="live-listViewBox">
			<ListViewVue :list="ListViewBox" width="65" height="65" font-size="25rpx" marginTop="-10rpx"></ListViewVue>
		</view>
		<view class="live-playlive">
			<TItleBoxVue title='好玩生活' SubTitle="更多"></TItleBoxVue>
			<view class="palyliveimage">
				<image src="../../static/live-palylive-image-1.png" mode=""></image>
				<view class="images">
					<image src="../../static/live-palylive-image-2.png" mode=""></image>
					<image src="../../static/live-palylive-image-3.png" mode=""></image>
				</view>
			</view>
		</view>
		<view class="live-serve">
			<TItleBoxVue title='便民服务' :icon="false"></TItleBoxVue>
			<view class="serveBox">
				<view class="serveListBox" v-for="(item,index) in serve" :key="index" :style="{background:`url(../../static/live-serve-${index+1}.png)`,backgroundSize:'100% 100%'}">
					<p>{{item.name}}</p>
					<span>{{item.subName}}</span>
				</view>
			</view>
		</view>
		<view class="live-PhoneNumber">
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
		<view class="live-infinite AllPage">
			<z-tabs :list="workTaber" :bar-style="{'background' : 'none'}" :tabs-style="{'background':'none',fontWeight: 'bold'}" :active-color='"#000"' bar-width='20rpx' bar-height='10rpx'></z-tabs>
			<view class="images">
				<image src="../../static/live-infinite-1.png" mode=""></image>
				<image src="../../static/live-infinite-2.png" mode=""></image>
				<image src="../../static/live-infinite-3.png" mode=""></image>
				<image src="../../static/live-infinite-4.png" mode=""></image>
			</view>
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
				listview:[
					{name:'生活缴费',subtitle:'轻松便捷',images:'../../static/live-icon-1.png'},
					{name:'政府服务',subtitle:'办事高效',images:'../../static/live-icon-2.png'},
					{name:'活动中心',subtitle:'精彩满满',images:'../../static/live-icon-3.png'},
				],
				ListViewBox:[
					{name:'我的能量分',images:'../../static/live-listview-icon-1.png'},
					{name:'惠加油',images:'../../static/live-listview-icon-2.png'},
					{name:'一键绑卡',images:'../../static/live-listview-icon-3.png'},
					{name:'签到',images:'../../static/live-listview-icon-4.png'},
					{name:'更多',images:'../../static/live-listview-icon-5.png'},
				],
				TopScroll:0,
				serve:[
					{name:'社保',subName:'电子社保'},
					{name:'医保',subName:'医保电子凭证'},
					{name:'诚易金',subName:'交易护航 资金保障'},
					{name:'个人信用报告',subName:'在线浏览 本地保存'},
				],
				workTaber:['精选','出现优惠'],
			};
		},
		components:{
			SearchTabVue,
			ListViewVue,
			TItleBoxVue
		},
		onPageScroll(TopScroll) {
			this.TopScroll =  TopScroll.scrollTop
		}
	}
</script>

<style lang="scss" scoped>
	.live{
		width: 100vw;
		min-height:100vh;
		background-color: #f6f7fb;
		background: url('../../static/live-bg-1.png')no-repeat;
		background-size: 100% 500rpx;
		padding-bottom: 50rpx;
		background-color: #f6f7fb;
		.live-listView{
			width: 95%;
			border-radius: 20rpx 20rpx  0 0;
			padding: 20rpx 0;
			margin: 0 auto;
			margin-top: 240rpx;
			z-index: 999;
			background-color: #fff;
			display: flex;
			.listView{
				display: flex;
				align-items: center;
				padding:0 20rpx;
				image{
					width: 60rpx;
					height: 60rpx;
					margin-right: 20rpx;
				}
				.TextView{
					p{
						font-weight: bold;
						font-size: 30rpx;
					}
					span{
						font-size: 25rpx;
						color: #888;
					}
				}
			}
			
		}
		.live-listViewBox{
			width: 95%;
			background-color: #fff;
			margin: 0 auto;
			border-radius: 0 0 20rpx 20rpx;
		}
		.live-playlive{
			padding: 20rpx 0;
			width: 95%;
			background-color: #fff;
			margin: 0 auto;
			border-radius: 20rpx;
			margin-top: 20px;
			.palyliveimage{
				
				margin-top: 20rpx;
				padding: 20rpx;
				display: flex;
				justify-content: space-between;
				image{
					width: 50%;
				}
				.images{
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					width: 48%;
					justify-content:space-between;
					image{
						width: 100%;
						height: 200rpx;
					}
				}
			}
		}
		.live-serve{
			padding: 20rpx 0;
			width: 95%;
			background-color: #fff;
			margin: 0 auto;
			border-radius: 20rpx;
			margin-top: 20px;
			.serveBox{
				display: flex;
				flex-wrap: wrap;
				justify-content: space-evenly;
				.serveListBox{
					margin-top: 20rpx;
					width: 46%;
					padding-bottom: 80rpx;
					border-radius: 20rpx;
					background: #f6f7fb;
					display: flex;
					flex-wrap: wrap;
					p{
						margin-top: 20rpx;
						padding:0 20rpx;
						font-size: 30rpx;
						width: 100%;
						font-weight: bold;
					}
					span{
						padding:0 20rpx;
						font-size: 25rpx;
						margin-top: 10rpx;
						color: #888;
					}
				}
			}
		}
		.live-PhoneNumber{
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
		.live-infinite{
			.images{
				display: flex;
				flex-wrap: wrap;
				justify-content: space-evenly;
				margin-top: 20rpx;
				image{
					width: 45%;
					height: 450rpx;
				}
			}
		}
	}
</style>
