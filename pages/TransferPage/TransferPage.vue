<template>
	<view class="Transfer AllPage">
		<loadTitleVue title='转账'></loadTitleVue>
		<view class="Transfer-MaxList">
			<view class="MaxList" v-for="(item,index) in MaxList" :key="index" @click="GetIndex(index)">
				<image :src="item.icon" mode=""></image>
				<span>{{item.name}}</span>
			</view>
		</view>
		<view class="Transfer-MaxList-Setting">
			<view  v-for="(item,index) in MaxListSet" @click="GetMaxListIndex(index)" :key="index+10" :style="{borderRight:index == 0 ? '1px solid #ccc' : ''}">
				{{item}}
			</view>
		</view>
		<ListViewVue :list="ListView" width="60" height="60" font-size="25rpx" @index='GetIndex'></ListViewVue>
		<view class="Transfer-people">
			<view class="people">
				<span>最近收款人</span>
				<view class="allPepole">
					全部 18
				</view>
			</view>
			<view class="people-list">
				<view class="lsitView">
					<view class="header-text">
						<image class="header" src="../../static/use-head-1.png" mode=""></image>
						<view>
							<span>吴志斐</span>
							<span class="text"></span>
						</view>
					</view>
					<image class="bottom" src="../../static/Transfer-bottom-1.png" mode=""></image>
				</view>
			</view>
			<view class="people-list" v-for="(item,index) in peopleList" :key="index">
				<view class="lsitView">
					<view class="header-text">
						<image class="header" :src="item.logo" mode=""></image>
						<view>
							<span>{{item.name}}</span>
							<span class="text">{{item.text}}</span>
						</view>
					</view>
					<image class="bottom" src="../../static/Transfer-bottom-1.png" mode=""></image>
				</view>
			</view>
		</view>
		
	</view>
</template>

<script>
	import loadTitleVue from '../../components/load-title.vue';
	import ListViewVue from '../../components/ListView.vue';
	export default {
		data() {
			return {
				MaxList:[
					{name:'银行卡转账',icon:'../../static/Transfer-MaxIcon-1.png'},
					{name:'手机号转账',icon:'../../static/Transfer-MaxIcon-2.png'}
				],
				MaxListSet:['转账记录','转账设置'],
				ListView:[
					{name:'信用卡还款',images:'../../static/Transfer-listView-1.png'},
					{name:'收款人管理',images:'../../static/Transfer-listView-2.png'},
					{name:'转账安全',images:'../../static/Transfer-listView-3.png'},
					{name:'日日盈',images:'../../static/Transfer-listView-4.png'},
				],
				peopleList:[
					{logo:'../../static/logo-1.png',name:'袁信亮',text:'中国建设银行总行(尾号8582)'},
					{logo:'../../static/logo-2.png',name:'唐曼',text:'中国邮政储蓄银行有限责任公司(尾号8923)'},
					{logo:'../../static/logo-3.png',name:'杨阳',text:'招商银行股份有限公司(尾号9123)'},
					{logo:'../../static/logo-4.png',name:'戴利川',text:'招商银行股份有限公司(尾号4612)'},
					{logo:'../../static/logo-5.png',name:'段银飞',text:'招商银行股份有限公司(尾号3321)'},
				]
			};
		},
		components:{
			loadTitleVue,
			ListViewVue
		},
		methods:{
			GetIndex(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/account-Transfer/account-Transfer'
				}) : ''
				index === 1 ? uni.navigateTo({
					url:'/pages/phone-Transfer/phone-Transfer'
				}) : ''
			},
			GetMaxListIndex(index){
				index === 0 ? uni.navigateTo({
					url:'/pages/Recording/Recording'
				}) : ''
			}
		}
	}
</script>

<style lang="scss">
	.Transfer{
		.Transfer-MaxList{
			width:95%;
			margin: 0 auto;
			background:url('@/static/Transfer-bg-1.png') ;
			background-size:100% 100% ;
			display: flex;
			justify-content: space-evenly;
			margin-top: 20rpx;
			.MaxList{
				display: flex;
				justify-content: center;
				text-align: center;
				padding: 30rpx 0;
				flex-wrap: wrap;
				color: #fff;
				font-size: 28rpx;
				image{
					width: 120rpx;
					height: 90rpx;
					margin-left: 30rpx;
				}
				span{
					width: 100%;
					margin-top: 10rpx;
				}
			}
		}
		.Transfer-MaxList-Setting{
			width: 95%;
			margin: 0 auto;
			padding: 20rpx 0;
			margin-bottom: 20rpx;
			background-color: #e6ebf2;
			display: flex;
			justify-content: space-evenly;
			border-radius: 0 0 20rpx 20rpx;
			view{
				display: flex;
				justify-content: center;
				flex: 1;
			}
		}
		.Transfer-listview{
			height: 100%;
			margin: 0 auto;
			margin-top: 30rpx;
			display: flex;
			align-items: center;
			position: relative;
			image{
				width: 28rpx;
				height: 18rpx;
				position: absolute;
				right: 20rpx;
				top: 40%;
				z-index: 999;
			}
		}
		.Transfer-people{
			width: 95%;
			margin: 0 auto;
			margin-top: 20rpx;
			.people{
				display: flex;
				align-items: center;
				justify-content: space-between;
				span{
					font-weight: bold;
					font-size: 38rpx;
				}
				.allPepole{
					display: flex;
					align-items: center;
					padding: 10rpx 20rpx;
					font-size: 28rpx;
					color: #5995ed;
					border-radius: 50rpx;
					background-color: #f5f7fa;
				}
			}
			.people-list{
				margin-top: 20rpx;
				.lsitView{
					display: flex;
					align-items: center;
					justify-content: space-between;
					margin-top: 20rpx;
					border-bottom: 1px solid #ddd;
					padding: 20rpx 0;
					.header-text{
						display: flex;
						align-items: center;
						
						.header{
							width: 80rpx;
							height: 80rpx;
						}
						view{
							display: flex;
							align-items: center;
							flex-wrap: wrap;
							padding:0 20rpx;
							span{
								font-weight: bold;
								font-size: 32rpx;
							}
							.text{
								width: 100%;
								font-size: 25rpx;
								margin-top: 10rpx;
								color: #888;
							}
						}
						
					}
					
					.bottom{
						width: 30rpx;
						height: 20rpx;
					}
				}
			}
		}
		
	}
</style>
