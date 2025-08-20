<template>
	<view class="load-datali">
		<view class="datali-title">
			<loadTitleVue title="个人经营性贷款" Text="提款信息" textColor="#b48636" :icon="false" titleFW='normal' @btn='GoList'></loadTitleVue>
		</view>
		<view class="money">
			<p>剩余未还本金(元)</p>
			<span>3,650,000.00</span>
			<text class="text">贷款金额:3,650,000.00元</text>
		</view>
		
		<view class="play-datali">
			<view class="p" v-for="(item,index) in play " :key="index" :style="{borderBottom:index === ListIndex ? '2px solid #c60127': 'none'}" @click="setIndex(index)">
				<p>{{item}}</p>
			</view>
			<view class="select">
				<p>筛选</p>
				<image src="../../static/load-select-1.png" mode=""></image>
			</view>
		</view>
		
		<scroll-view scroll-y="true" style="height: 70vh;" >
			<playVue v-if="ListIndex === 0"></playVue>
			
			<dataliVue v-if="ListIndex === 1"></dataliVue>
		</scroll-view>
		
		
	</view>
</template>

<script>
	import loadTitleVue from '../../components/load-title.vue';
	import playVue from '../../components/play.vue';
	import dataliVue from '../../components/datali.vue';
	export default {
		data() {
			return {
				play:['待还计划','还款记录'],
				ListIndex:0
			};
		},
		components:{
			loadTitleVue,
			playVue,
			dataliVue
		},
		methods:{
			setIndex(index){
				this.ListIndex = index
			},
			GoList(){
				uni.navigateTo({
					url:'/pages/load-list/load-list'
				})
			}
		},
	}
</script>

<style lang="scss">
	.load-datali{
		width: 100vw;
		min-height:100vh;
		background-size:100%;
		background-color: #f2f2f2;
		.datali-title{
			background-color: #fff;
			margin-top: 50rpx;
			padding: 0 20rpx;
		}
		.money{
			display: flex;
			flex-wrap: wrap;
			justify-content: center;
			text-align: center;
			background-color: #fff;
			padding: 50rpx;
			p{
				font-size: 30rpx;
			}
			span{
				width: 100%;
				font-weight: bold;
				font-size: 60rpx;
				margin-top: 15rpx;
			}
			.text{
				width: 100%;
				color: #888;
				font-size: 28rpx;
			}
		}
		.play-datali{
			background-color: #fff;
			border-bottom: 1px solid #ddd;
			margin-top: 20rpx;
			justify-content: center;
			align-items: center;
			display: flex;
			.p{
				width: 30%;
				display: flex;
				align-items: center;
				justify-content: center;
				border-bottom:2px solid #c60127 ;
				padding: 20rpx;
				p{
					font-weight: bold;
					color: #444444;
				}
			}
			.select{
				width: 20%;
				display: flex;
				align-items: center;
				justify-content: center;
				image{
					width: 40rpx;
					height: 40rpx;
				}
			}
		}
	}
</style>
