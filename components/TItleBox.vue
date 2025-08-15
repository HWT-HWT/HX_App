<template>
	<view class="TitleBox">
		<span :style="{fontSize:titleSize}" >{{title}}</span>
		<view class="text" :style="{color:textColor}">{{SubTitle}} <image v-if="icon" :src='images' mode=""></image> </view>
	</view>
</template>

<script>
	export default {
		name:"TItleBox",
		data() {
			return {
				
			};
		},
		props:{
			title:{
				type:String,
			},
			titleSize:{
				type:String
			},
			SubTitle:{
				type:String,
			},
			icon:{
				type:Boolean,
				default:true
			},
			images:{
				type:String,
				default:'../../static/upsdk_payment_right.webp'
			},
			textColor:{
				type:String,
				default:'#000'
			}
		}
	}
</script>

<style lang="scss" scoped>
	.TitleBox{
		padding:0 20rpx;
		display: flex;
		justify-content: space-between;
		align-items: center;
		span{
			font-weight: bold;
			font-size: 35rpx;
		}
		.text{
			font-size: 25rpx;
			display: flex;
			align-items: center;
			color: #333;
			image{
				width: 35rpx;
				height: 35rpx;
			}
		}
	}
</style>