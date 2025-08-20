<template>
	<view class="play">
		<view class="play-list">
			<view class="play-left">
				<view class="checkbox">
					<image src="../static/list-play-1.png" class="one" mode=""></image>
					<image src="../static/list-play-2.png" class="two" mode=""></image>
				</view>
				<view class="time">
					2025-09-20
				</view>
			</view>
			<view class="play-right">
				<view class="Right-money">
					<p>￥12,090.00</p>
					<view class="span">本金0.00 + 利息 12,090.00</view>
				</view>
			</view>
		</view>
		<view class="play-list" v-for="(item,index) in list" :key="index">
			<view class="play-left">
				<view class="checkbox">
					<image src="../static/list-play-3.png" class="one" mode=""></image>
					<image src="../static/list-play-4.png" class="two" mode=""></image>
				</view>
				<view class="time color">
					{{item.data}}
				</view>
			</view>
			<view class="play-right">
				<view class="Right-money">
					<p class="color">￥{{item.money}}</p>
					<view class="span color">{{item.ArrMoney}}</view>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "play",
		data() {
			return {
				list:[
					{data:'2025-10-20',money:'11,700.00',ArrMoney:'本金0.00 + 利息 11,700.00'},
					{data:'2025-11-20',money:'12,090.00',ArrMoney:'本金0.00 + 利息 12,090.00'},
					{data:'2025-12-20',money:'11,700.00',ArrMoney:'本金0.00 + 利息 11,700.00'},
					{data:'2026-01-20',money:'62,090.00',ArrMoney:'本金50,000.00 + 利息 12,090.00'},
					{data:'2026-02-20',money:'12,045.00',ArrMoney:'本金0.00 + 利息 12,045.00'},
					{data:'2026-03-20',money:'10,880.00',ArrMoney:'本金0.00 + 利息 10,880.00'},
					{data:'2026-04-20',money:'12,045.00',ArrMoney:'本金0.00 + 利息 12,045.00'},
					{data:'2026-05-20',money:'11,657.00',ArrMoney:'本金0.00 + 利息 11,657.00'},
					{data:'2026-06-20',money:'12,045.00',ArrMoney:'本金0.00 + 利息 12,045.00'},
					{data:'2026-07-20',money:'61,657.00',ArrMoney:'本金50,000.00 + 利息 11,657.00'},
					{data:'2026-08-20',money:'12,001.00',ArrMoney:'本金0.00 + 利息 12,001.00'},
					{data:'2026-09-20',money:'12,001.00',ArrMoney:'本金0.00 + 利息 12,001.00'},
					{data:'2026-10-20',money:'11,614.00',ArrMoney:'本金0.00 + 利息 11,614.00'},
					{data:'2026-11-20',money:'12,001.00',ArrMoney:'本金0.00 + 利息 12,001.00'},
					{data:'2026-12-20',money:'11,614.00',ArrMoney:'本金0.00 + 利息 11,614.00'},
					{data:'2027-01-20',money:'62,001.00',ArrMoney:'本金50,000.00 + 利息 12,001.00'},
					{data:'2027-02-20',money:'11,957.00',ArrMoney:'本金0.00 + 利息 11,957.00'},
					{data:'2027-03-20',money:'10,800.00',ArrMoney:'本金0.00 + 利息 10,800.00'},
					{data:'2027-04-20',money:'11,957.00',ArrMoney:'本金0.00 + 利息 11,957.00'},
					{data:'2027-05-20',money:'11,571.00',ArrMoney:'本金0.00 + 利息 11,571.00'},
					{data:'2027-06-20',money:'11,957.00',ArrMoney:'本金0.00 + 利息 11,957.00'},
					{data:'2027-06-27',money:'3,502,700.00',ArrMoney:'本金3,500,000.00 + 利息 2.700.00'},
				]
			};
		}
	}
</script>

<style lang="scss" scoped>
	.play {
		margin-top: 20rpx;
		.play-list {
			padding: 0 40rpx;
			display: flex;
			justify-content: space-between;

			.play-left {
				display: flex;

				.checkbox {
					margin-top: 30rpx;
					width: 25rpx;
					display: flex;
					flex-wrap: wrap;
					align-items: center;
					justify-content: center;

					.one {
						width: 25rpx;
						height: 25rpx;
					}

					.two {
						width: 12rpx;
						height: 100rpx;
						margin-top: 10rpx;
					}
				}

				.time {
					padding: 25rpx;
					font-weight: bold;
					font-size: 26rpx;
				}

				.color {
					color: #888;
				}
			}

			.Right-money {
				padding: 20rpx;
				text-align: right;

				p {
					font-size: 32rpx;
					font-weight: bold;
				}

				.span {
					color: #888;
					margin-top: 20rpx;
					font-size: 25rpx;
				}

				.color {
					color: #888;
				}
			}
		}
	}
</style>