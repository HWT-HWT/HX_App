<template>
	<view>
		<view class="SearchTab" :style="{opacity: topScollct/100 ? 0 : 1}">
			<image class="icon" v-if="leftIcon" :src="leftImage" mode="" :style="{width: leftwidth, height:leftheight}"></image>
			<view class="Search">
				<image src="@/static/Search.png" mode=""></image>
				<input type="text" value="远程银行" />
				<text>搜索</text>
			</view>
			<image :style="{width:rightwidth,height:rightheight}"  class="icon" v-for="(item,index) in rightImage" :key='index' :src="item" mode=""></image>
		</view>
		
		<view class="SearchTab position"  :style="{opacity: topScollct/100}">
			<image class="icon" :src="leftImage" mode="" :style="{width: leftwidth, height:leftheight}" ></image>
			<view class="Search">
				<image src="@/static/Search.png" mode=""></image>
				<input type="text" value="远程银行" />
				<text>搜索</text>
			</view>
			<image :style="{width:rightwidth,height:rightheight}" class="icon" v-for="(item,index) in rightImage" :key='index' :src="item" mode=""></image>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		props:{
			topScollct:{
				type:Number,
				default:0
			},
			leftImage:{
				type:String,
				default:'../../static/SearchTab-1.png'
			},
			rightImage:{
				type:[Object,Array],
				default: function(){
					return ['../../static/SearchTab-2.png','../../static/SearchTab-3.png']
				}
			},
			leftwidth:{
				type:String,
				default:'50rpx'
			},
			leftheight:{
				type:String,
				default:'50rpx'
			},
			
			rightwidth:{
				type:String,
				default:'50rpx'
			},
			rightheight:{
				type:String,
				default:'50rpx'
			},
			leftIcon:{
				type:Boolean,
				default:true
			}
		}
	}
</script>

<style lang="scss" scoped>
	.SearchTab{
		padding: 20rpx;
		padding-top:70rpx;
		display: flex;
		align-items: center;
		.icon{
			width: 50rpx;
			height: 50rpx;
			padding: 10rpx;
		}
		.Search{
			flex: 1;
			
			border-radius: 10rpx;
			background-color: #fff;
			margin:20rpx;
			display: flex;
			align-items: center;
			font-size: 28rpx;
			image{
				width: 35rpx;
				height:35rpx;
				padding: 15rpx;
			}
			input{
				flex: 1;
				margin-left: 20rpx;
				font-size: 28rpx;
			}
			text{
				padding:0 10rpx;
			}
		}
	}
	.position{
		width: 95%;
		position: fixed;
		background-color: #fff;
		z-index: 999;
		top: 0;
	}
</style>
