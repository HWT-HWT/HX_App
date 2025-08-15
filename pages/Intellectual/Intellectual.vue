<template>
	<view class="Intellectual">
		<view class="title">
			<loadTitleVue title='资产概览'></loadTitleVue>
		</view>
		<view class="date">更新时间: 08-05 10:41:45</view>
		<view class="Intellectual-moenyBox">
			<span>总资产(元)</span>
			<p>0.00</p>
			<text>查看收益</text>
		</view>
		<view class="Intellectual-list">
			<view class="name" v-for="(item,index) in list" :key="index" :style="{marginTop:index > 2 ? '20rpx' : '0', borderRadius:index > 2 ? '20rpx' : '0',}">
				<view>
					<span>{{item.name}}</span>
					<image src="@/static/Intellectual-icon-1.png" mode=""></image>
				</view>
				<view class="SubNumber">
					<span>{{item.money}}</span>
					<image class="right" src="@/static/upsdk_payment_right.webp" mode=""></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	import loadTitleVue from '../../components/load-title.vue';
	export default {
		data() {
			return {
				list:[
					{name:'存款',money:'0.00'},
					{name:'人民币存款',money:'0.00'},
					{name:'外币存款',money:'0.00'},
					{name:'理财',money:'0.00'},
					{name:'基金',money:'0.00'},
					{name:'信托',money:'0.00'}
				]
			};
		},
		components:{
			loadTitleVue
		}
		
	}
</script>

<style lang="scss" scoped>
.Intellectual{
	width: 100vw;
	height: 100vh;
	background: url('@/static/Intellectual-bg-1.png') no-repeat;
	background-color:#f6f8fc ;
	background-size:100%;
	.title{
		padding-top: 40rpx;
	}
	.date{
		width: 100%;
		text-align: center;
		color: #888;
		font-size: 25rpx;
		margin-top: 20rpx;
	}
	.Intellectual-moenyBox{
		width: 92%;
		
		border-radius: 20rpx;
		line-height: 50rpx;
		margin: 0 auto;
		text-align: center;
		background-color: #fff;
		padding: 30rpx 0;
		margin-top: 50rpx;
		span{
			font-size: 30rpx;
		}
		p{
			font-size: 50rpx;
			font-weight: bold;
			margin: 20rpx 0;
		}
		text{
			color: #87b2f3;
			font-size: 25rpx;
		}
	}
	.Intellectual-list{
		margin-top: 20rpx;
		display: flex;
		flex-wrap: wrap;
		.name{
			width: 92%;
			margin: 0 auto;
			background-color: #fff;
			border-radius: 20rpx;
			display: flex;
			justify-content: space-between;
			padding: 20rpx 0;
			view{
				padding: 0 20rpx;
				display: flex;
				align-items: center;
				justify-content: center;
			}
			span{
				padding: 30rpx;
				font-size: 32rpx;
				font-weight: bold;
			}
			image{
				width: 30rpx;
				height: 20rpx;
				margin-left: -20rpx;
			}
			.right{
				width: 40rpx;
				margin-left: -20rpx;
				height: 40rpx;
			}
		}
	}
}
</style>
