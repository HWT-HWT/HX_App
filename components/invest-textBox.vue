<template>
	<view class="wealth-invest-textBox" >
		<view class="Optimal-money" :style="{'borderBottom': list.border ? '1px solid #ccc' : ''}">
			<view class="money-title" v-if="list.title">
				<span>{{list.title}}</span>
				<text>更多 <image src="../static/dis_renwu_next.png" mode=""></image> </text>
			</view>
			<view class="money-Subtitle">
				{{list.Subtitle}}
			</view>
			<view class="Optimal-list">
				<view class="Optimal-list-left">
					<p class="Optimal-list-left-MaxTitle">{{list.leftTop}}</p>
					<p class="Optimal-list-left-MiniTitle">{{list.leftBottom}}</p>
				</view>	
				<view class="Optimal-list-rigth">
					<p class="Optimal-list-left-MaxTitle">{{list.rigthTop}}</p>
					<p class="Optimal-list-left-MiniText">
						<text :style="{'borderRight' : index+1 === list.rigthBottom.length ? 'none' :'1px solid #ccc'}" v-for="(item,index) in list.rigthBottom" :key="index">{{item}}</text>
					</p>
				</view>
				<view class="btn" v-if="btn">
					去看看
				</view>
			</view>
			<view class="Optimal-bottom" v-if="list.Optimal">
				<p>{{list.Optimal}}</p>
			</view>
			<view class="Optimal-tisi" v-if="list.tisiText || list.tisiFooter">
				<view class="Optimal-tisi-text-icon" v-if="list.tisiText">
					<view class="tisi-text">
						{{list.tisiText}}
					</view>
					<view class="tisi-icon">
						<image  mode=""></image>
					</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"invest-textBox",
		data() {
			return {
				
			};
		},
		props:{
			list:{
				type:[Object,Array]
			},
			btn:{
				type:Boolean,
				default:false
			}
		}
	}
</script>

<style lang="scss" scoped>
	.wealth-invest-textBox{
		width: 90%;
		margin: 0 auto;
		padding-bottom:10rpx;
		.Optimal-money{
			width: 100%;
			margin-top: 20rpx;
			padding-bottom:10rpx;
			.money-title{
				width:100%;
				margin: 10rpx auto;
				font-size: 28rpx;
				display: flex;
				justify-content: space-between;
				text{
					font-size: 25rpx;
					image{
						width: 20rpx;
						height: 20rpx;
						margin-left: 10rpx;
					}
				}
				.uni-tag{
					background-color: #eff6ff; border-color: #eff6ff; color: #2979ff; font-weight:bold;
				}
			}
			.money-Subtitle{
				font-weight: bold;
				font-size: 25rpx;
				margin-top: 20rpx;
			}
			.Optimal-list{
				width: 100%;
				margin: 0 auto;
				display: flex;
				align-items: center;
				.Optimal-list-left{
					flex: 1;
					.Optimal-list-left-MaxTitle{
						font-size: 40rpx;
						color: #cd242e;
						font-weight: bold;
						margin: 10rpx auto;
					}
					.Optimal-list-left-MiniTitle{
						font-size: 20rpx;
						color: #888;
					}
				}
				.Optimal-list-rigth{
					flex: 1;
					.Optimal-list-left-MaxTitle{
						font-size: 28rpx;
						font-weight: bold;
						margin: 10rpx auto;
						padding: 0 15rpx;
					}
					.Optimal-list-left-MiniText{
						font-size: 20rpx;
						color: #888;
						text{
							padding: 0 15rpx;
						}
					}
				}
				.btn{
					border: 1px solid;
					padding:10rpx 20rpx;
					font-size: 25rpx;
					color: #fff;
					background-color: #dc101c;
					border-radius: 50rpx;
				}
			}
			.Optimal-bottom{
				font-size: 25rpx;
				color: #555;
				
			}
			.Optimal-tisi{
				width: 100%;
				background-color: #f2f2f2;
				.Optimal-tisi-text-icon{
					width: 100%;
					display: flex;
					justify-content: space-between;
					margin-top: 10rpx;
					padding: 10rpx;
					.tisi-text{
						width: 90%;
						color: #666;
						font-size: 20rpx;
					}
					.tisi-icon{
						flex: 1;
						transform: rotateZ(90deg);
						display: flex;
						justify-content: center;
						align-self: self-start;
						image{
							width: 25rpx;
							height: 25rpx;
						}
					}
				}
				p{
					font-size: 23rpx;
					padding:10rpx;
					display: flex;
					align-items: center;
				}
			}
		}
	}
</style>