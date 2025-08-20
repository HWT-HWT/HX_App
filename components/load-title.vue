<template>
	<view class="load-title" style="padding-top: 80rpx;">
		<image class="left-icon" src="@/static/left-cion-1.png" mode="" @click="Back"></image>
		<text :style="{fontWeight:titleFW}">{{title}}</text>
		<view class="icon">
			<image src="@/static/server-1.png" mode="" v-if="icon"></image>
			<text :style="{color:textColor}" @click="btn">{{Text}}</text>
		</view>
	</view>
</template>

<script>
	export default {
		name:"load-title",
		data() {
			return {
				
			};
		},
		methods:{
			Back(){
				uni.navigateBack()
			},
			btn(){
				this.$emit('btn')
			}
		},
		props:{
			title:{
				type:String,
				default:''
			},
			icon:{
				type:Boolean,
				default:true
			},
			Text:{
				type:String,
				default:''
			},
			textColor:{
				type:String,
				default:'#000'
			},
			titleFW:{
				type:String,
				default:'bold'
			}
		}
	}
</script>

<style lang="scss">
	.load-title{
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding-top: 150rpx;
		.left-icon{
			width: 35rpx;
			height: 45rpx;
		}
		text{
			font-size: 35rpx;
			font-weight: bold;
		}
		.icon{
			display: flex;
			align-items: center;
			image{
				width: 65rpx;
				height: 65rpx;
			}
			text{
				font-weight: normal;
				font-size: 25rpx;
			}
		}
	}
</style>