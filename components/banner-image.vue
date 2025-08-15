<template>
	<view class="index-banner">
		<swiper :indicator-dots="true" :autoplay="true" :interval="3000" :duration="1000">
			<swiper-item v-for="(item,index) in images" :key="index">
				<image :src="item" mode=""></image>
			</swiper-item>
		</swiper>
	</view>
</template>

<script>
	export default {
		name:"banner-image",
		data() {
			return {
				
			};
		},
		props:{
			images:{
				type:Array,
			}
		}
	}
</script>

<style lang="scss" scoped>
.index-banner{
	width: 90%;
	margin: 0 auto;
	margin-top: 30rpx;
	height: 170rpx;
	swiper{
		width: 100%;
		height: 100%;
		::v-deep.uni-swiper-dot{
			width: 10rpx;
			height: 10rpx;
			border-radius: 0;
			background-color: #ad8e85;
		}
		::v-deep.uni-swiper-dot-active{
			width: 10rpx;
			height: 10rpx;
			border-radius: 0;
			background-color: #000;
		}
		swiper-item{
			image{
				width: 100%;
				height: 170rpx;
			}
		}
		
	}
}
</style>