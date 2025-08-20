<template>
	<view class="load-two">
		<view class="load-title">
			<image class="left-icon" src="@/static/left-cion-1.png" mode=""></image>
			<text>我的贷款</text>
			<view class="icon">
				<image src="@/static/server-1.png" mode=""></image>
			</view>
		</view>
		<view class="load-content">
			<view class="content-listView">
				<view class="listView" v-for="(item,index) in listcontent" :key="index" :style="{borderRight:index+1 === listcontent.length ? 'none':'1px solid #fff'}">
					<image :src="item.bg"  mode=""></image>
					<span>{{item.name}}</span>
				</view>
			</view>
			<view class="title">
				<span>龙商贷</span>
				<view class="subTitle">
					华夏精选
				</view>
			</view>
			<view class="datali">
				<view class="dataliView">
					<p>最高可贷（元）</p>
					<span>￥500万</span>
				</view>
				<view class="dataliView">
					<p>借款方式</p>
					<span class="color">随借随用</span>
				</view>
			</view>
			<view class="btn">
				立即申请
			</view>
		</view>
		<view class="load-Goods">
			<TItleBoxVue title="精选产品" :icon='false'></TItleBoxVue>
			<view class="host-view">
				<view class="textView">
					<view class="p"> 
						<image src="../static/load-two-icon-4.png" mode=""></image>
						<p>房抵贷</p>
						<view class="subTitle">
							智能评估
						</view>
						<view class="subTitle">
							在线抵押
						</view>
					</view>
					<p class="text">最高可贷(元)</p>
					<p class="span">3,000万</p>
				</view>
				<view class="btnView">
					去申请
				</view>
			</view>
			<view class="host-view">
				<view class="textView">
					<view class="p"> 
						<image src="../static/load-two-icon-5.png" mode=""></image>
						<p>经营贷</p>
						<view class="subTitle">
							效率高
						</view>
						<view class="subTitle">
							试用广
						</view>
					</view>
					<p class="text">最高可贷(元)</p>
					<p class="span">2,000万</p>
				</view>
				<view class="btnView">
					去申请
				</view>
			</view>
			<view class="host-view">
				<view class="textView">
					<view class="p"> 
						<image src="../static/load-two-icon-6.png" mode=""></image>
						<p>市场贷</p>
						<view class="subTitle">
							额度高
						</view>
						<view class="subTitle">
							用款灵
						</view>
					</view>
					<p class="text">最高可贷(元)</p>
					<p class="span">2,000万</p>
				</view>
				<view class="btnView">
					去申请
				</view>
			</view>
		</view>
		<!-- <view class="load-host">
			<TItleBoxVue title="热门产品" :icon='false'></TItleBoxVue>
		</view> -->
	</view>
</template>

<script>
	import TItleBoxVue from './TItleBox.vue';
	export default {
		name:"load-two",
		data() {
			return {
				listcontent:[
					{name:'数字化办理',bg:'../../static/load-two-icon-1.png'},
					{name:'纯信用',bg:'../../static/load-two-icon-2.png'},
					{name:'快速审批',bg:'../../static/load-two-icon-3.png'},
				]
			};
		},
		components:{
			TItleBoxVue
		}
	}
</script>

<style lang="scss">
	.load-two{
		width: 100vw;
		min-height:100vh;
		background: url('../static/load-two-bg-1.png')no-repeat;
		background-size:100%;
		.load-title{
			padding: 80rpx 30rpx;
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
		.load-content{
			background: url('../static/load-two-bg-2.png')no-repeat;
			width: 95%;
			padding-bottom: 50rpx;
			background-size: 100% 100%;
			margin: 0 auto;
			margin-top: 200rpx;
			.content-listView{
				padding: 20rpx 30rpx;
				display: flex;
				justify-content: space-between;
				.listView{
					width: 33%;
					height: 20rpx;
					color: #fff;
					display: flex;
					align-items: center;
					border-right: 1px solid #fff;
					margin-top: 10rpx;
					justify-content: center;
					image{
						width: 40rpx;
						height: 40rpx;
					}
					span{
						font-size: 28rpx;
						margin: 0 10rpx;
					}
				}
			}
			.title{
				width: 100%;
				display: flex;
				justify-content: center;
				align-items: center;
				margin-top: 30rpx;
				span{
					font-size: 38rpx;
					font-weight: bold;
					margin-left: 50rpx;
				}
				.subTitle{
					border: 1px solid ;
					font-size: 22rpx;
					margin-left: 10rpx;
					color: #e56068;
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
			.btn{
				width: 90%;
				background-color: #669aff;
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
		.load-Goods{
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
					.p{
						
						display: flex;
						align-items: center;
						image{
							width: 30rpx;
							height: 30rpx;
							margin: 0 10rpx;
						}
						p{
							font-weight: bold;
							font-size: 32rpx;
						}
						.subTitle{
							font-size: 20rpx;
							border: 1px solid;
							color: #da1e29;
							margin: 0 10rpx;
							padding:2rpx 5rpx;
						}
					}
					.text{
						font-size: 25rpx;
						margin: 20rpx auto;
					}
					.span{
						font-weight: bold;
						font-size: 50rpx;
					}
				}
				.btnView{
					padding:5rpx 20rpx;
					margin: 0 30rpx;
					font-size: 26rpx;
					border-radius: 50rpx;
					border: 1px solid #7e7e7e;
					color: #000;
					margin-top: 50rpx;
				}
			}
		}
		.load-host{
			margin-top: 20rpx;
		}
	}
</style>