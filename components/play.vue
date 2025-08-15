<template>
	<view class="play">
		<view class="play-list">
			<view class="play-left">
				<view class="checkbox">
					<image src="../static/list-play-1.png" class="one" mode=""></image>
					<image src="../static/list-play-2.png" class="two" mode=""></image>
				</view>
				<view class="time">
					2025-08-20
				</view>
			</view>
			<view class="play-right">
				<view class="Right-money">
					<p>￥42,315.00</p>
					<view class="span">本金0.00 + 利息 42,315.00</view>
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
					{data:'2025-09-20',money:'42,315.00',ArrMoney:'本金0.00 + 利息 42,315.00'},
					{data:'2025-10-20',money:'40,950.00',ArrMoney:'本金0.00 + 利息 40,950.00'},
					{data:'2025-11-20',money:'42,315.00',ArrMoney:'本金0.00 + 利息 42,315.00'},
					{data:'2025-12-20',money:'40,950.00',ArrMoney:'本金0.00 + 利息 40,950.00'},
					{data:'2026-01-20',money:'92,315.00',ArrMoney:'本金50,000.00 + 利息 42,315.00'},
					{data:'2026-02-20',money:'42,160.00',ArrMoney:'本金0.00 + 利息 42,160.00'},
					{data:'2026-03-20',money:'38,080.00',ArrMoney:'本金0.00 + 利息 38,080.00'},
					{data:'2026-04-20',money:'42,160.00',ArrMoney:'本金0.00 + 利息 42,160.00'},
					{data:'2026-05-20',money:'40,800.00',ArrMoney:'本金0.00 + 利息 40,800.00'},
					{data:'2026-06-20',money:'42,160.00',ArrMoney:'本金0.00 + 利息 42,160.00'},
					{data:'2026-07-20',money:'90,800.00',ArrMoney:'本金50,000.00 + 利息 40,800.00'},
					{data:'2026-08-20',money:'42,005.00',ArrMoney:'本金0.00 + 利息 42,005.00'},
					{data:'2026-09-20',money:'42,005.00',ArrMoney:'本金0.00 + 利息 42,005.00'},
					{data:'2026-10-20',money:'40,650.00',ArrMoney:'本金0.00 + 利息 40,650.00'},
					{data:'2026-11-20',money:'42,005.00',ArrMoney:'本金0.00 + 利息 42,005.00'},
					{data:'2026-12-20',money:'40,650.00',ArrMoney:'本金0.00 + 利息 40,650.00'},
					{data:'2027-01-20',money:'92,005.00',ArrMoney:'本金50,000.00 + 利息 42,005.00'},
					{data:'2027-02-20',money:'41,850.00',ArrMoney:'本金0.00 + 利息 41,850.00'},
					{data:'2027-03-20',money:'37,800.00',ArrMoney:'本金0.00 + 利息 37,800.00'},
					{data:'2027-04-20',money:'41,850.00',ArrMoney:'本金0.00 + 利息 41,850.00'},
					{data:'2027-05-20',money:'40,500.00',ArrMoney:'本金0.00 + 利息 40,500.00'},
					{data:'2027-06-20',money:'41,850.00',ArrMoney:'本金0.00 + 利息 41,850.00'},
					{data:'2027-06-20',money:'13,509,450.00',ArrMoney:'本金13,500,000.00 + 利息 9,450.00'},
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