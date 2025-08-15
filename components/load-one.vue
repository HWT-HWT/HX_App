<template>
	<view class="load-one">
		<loadTitleVue title='我的贷款'></loadTitleVue>

		<view class="load-Coupons">
			<view class="Coupons-view">
				<image src="@/static/Coupons-icon-1.png" mode=""></image>
				<span>我的优惠卷</span>
			</view>
			<view class="Coupons-menu">
				<span>立即查看</span>
				<image src="@/static/upsdk_payment_right.webp" mode=""></image>
			</view>
		</view>
		<view class="load-datali">
			<view class="title">
				<p>龙e贷</p>
			</view>
			<view class="datali">
				<view class="dataliView">
					<p>最高可贷（元）</p>
					<span>￥500,000</span>
				</view>
				<view class="dataliView">
					<p>年化利率(单利)低至</p>
					<span class="color">3.50%</span>
				</view>
			</view>
			<view class="list-span">
				<view class="span">
					随借随还
				</view>
				<view class="span">
					按日还息
				</view>
				<view class="span" style="border-right: none;">
					期限灵活
				</view>
			</view>
			
			<view class="btn">
				立即申请
			</view>
		</view>
		<view class="load-Host">
			<TItleBoxVue title="热门产品" :icon='false'></TItleBoxVue>
			<view class="host-view">
				<view class="textView">
					<p>安居贷</p>
					<span>最高可贷100万 场景消费专属</span>
				</view>
				<view class="btnView">
					去申请
				</view>
			</view>
			
			<view class="host-view">
				<view class="textView">
					<p>菁英e贷</p>
					<span>最高可贷50万 优质客户专属</span>
				</view>
				<view class="btnView">
					去申请
				</view>
			</view>
		</view>
		<view class="load-Host">
			<TItleBoxVue title="特色产品" :icon='false'></TItleBoxVue>
			<view class="host-view">
				<view class="textView">
					<p>新市民菁英e贷</p>
					<span>最高可贷50万 新市民专属</span>
				</view>
				<view class="btnView">
					去申请
				</view>
			</view>
			
			<view class="host-view">
				<view class="textView">
					<p>阳光华夏个人消费e贷</p>
					<span>阳光保险客户专属网贷产品</span>
				</view>
				<view class="btnView">
					去申请
				</view>
			</view>
		</view>
		<view class="load-Setting">
			<TItleBoxVue title="贷款小工具" :icon='false'></TItleBoxVue>
			<view class="little-Setting">
				<view class="little" v-for="(item,index) in 3" :key="index" :style="{background:`url(../static/load-one-bg-${index+2}.png)`,backgroundSize:'100% 100%'}">
					<p>贷款利率表</p>
					<span>最新LRP 一目了然</span>
				</view>
			</view>
		</view>
	</view>
</template>
<script>
	import TItleBoxVue from './TItleBox.vue';
	import loadTitleVue from './load-title.vue';
	export default {
		name:"load-one",
		data() {
			return {
				
			};
		},
		components:{
			TItleBoxVue,
			loadTitleVue
		}
	}
</script>

<style lang="scss">
	.load-one{
		width: 100vw;
		min-height:100vh;
		background: url('../static/load-bg-2.png')no-repeat;
		background-size:100%;
		.load-title{
			padding: 50rpx 30rpx;
			display: flex;
			align-items: center;
			justify-content: space-between;
			.left-icon{
				width: 35rpx;
				height: 45rpx;
			}
			text{
				font-size: 35rpx;
				font-weight: bold;
			}
			.icon{
				image{
					width: 65rpx;
					height: 65rpx;
				}
			}
		}
		.load-Coupons{
			width: 95%;
			margin: 0 auto;
			border-radius: 20rpx;
			background-color: #fff;
			display: flex;
			justify-content: space-between;
			margin-top: 240rpx;
			.Coupons-view{
				padding: 25rpx 10rpx;
				display: flex;
				align-items: center;
				image{
					margin: 0 30rpx;
					width: 60rpx;
					height: 60rpx;
				}
				span{
					font-size: 32rpx;
				}
			}
			.Coupons-menu{
				padding: 20rpx 10rpx;
				display: flex;
				align-items: center;
				image{
					margin-top: 5rpx;
					width: 50rpx;
					height: 50rpx;
				}
				span{
					font-size: 28rpx;
				}
			}
		}
		.load-datali{
			width: 95%;
			margin: 0 auto;
			background: url('@/static/load-one-bg-1.png');
			background-size: 100% 100%;
			margin-top: 30rpx;
			padding: 60rpx 0;
			.title{
				display: flex;
				justify-content: center;
				p{
					font-size: 35rpx;
					font-weight: bold;
				}
			}
			.datali{
				margin-top: 50rpx;
				display: flex;
				.dataliView{
					width: 50%;
					display: flex;
					flex-wrap: wrap;
					justify-content: center;
					text-align: center;
					p{
						width: 100%;
						font-size: 25rpx;
					}
					span{
						font-size: 50rpx;
						font-weight: bold;
						margin-top: 10rpx;
					}
					.color{
						color: #d80c18;
					}
				}
			}
			.list-span{
				margin-top: 40rpx;
				display: flex;
				align-items: center;
				justify-content: center;
				.span{
					height: 30rpx;
					font-size: 25rpx;
					border-right: 1px solid;
					color: #888;
					padding: 0 20rpx;
				}
			}
			.btn{
				width: 90%;
				background-color: #db0e1c;
				color: #fff;
				margin: 0 auto;
				display: flex;
				justify-content: center;
				font-size: 32rpx;
				font-weight: bold;
				margin-top: 40rpx;
				border-radius: 50rpx;
				padding: 20rpx 0;
			}
		}
		.load-Host{
			margin-top: 20rpx;
			.host-view{
				width: 95%;
				margin: 0 auto;
				display: flex;
				align-items: center;
				justify-content: space-between;
				background-color: #fff;
				margin-top: 20rpx;
				border-radius: 20rpx;
				.textView{
					padding: 30rpx;
					p{
						font-weight: bold;
						font-size: 32rpx;
					}
					span{
						color: #dd2b36;
						font-size: 20rpx;
					}
				}
				.btnView{
					padding:5rpx 20rpx;
					margin: 0 30rpx;
					font-size: 26rpx;
					border-radius: 50rpx;
					border: 1px solid #7e7e7e;
					color: #000;
				}
			}
		}
		.load-Setting{
			margin-top: 20rpx;
			.little-Setting{
				width: 95%;
				margin: 0 auto;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				.little{
					width: 48%;
					background: url('@/static/load-one-bg-2.png')no-repeat;
					background-size: 100% 100%;
					padding-bottom: 70rpx;
					margin-top: 20rpx;
					p{
						font-weight: bold;
						font-size: 32rpx;
						padding: 10rpx 20rpx;
						padding-top: 30rpx;
					}
					span{
						padding:20rpx;
						font-size: 25rpx;
						color: #888;
					}
				}
			}
		}
	}
</style>