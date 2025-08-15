<template>
	<view class="datali">
		<p>支持查询近五年内还款记录</p>
		<view class="list-datali" v-for="(item,index) in list" :key="index">
			<view class="datali-money">
				<span>还款金额{{item.money}}元</span>
				<text>{{item.arrMoney}}</text>
			</view>
			<view class="text">
				{{item.data}}
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"datali",
		data() {
			return {
				list:[
					{money:'215.89',arrMoney:'本金0.00 利息 215.89',data:'2025-07-20'},
					{money:'215.89',arrMoney:'本金0.00 利息 215.89',data:'2025-06-20'},
					{money:'215.89',arrMoney:'本金0.00 利息 215.89',data:'2025-05-20'},
					{money:'215.89',arrMoney:'本金0.00 利息 215.89',data:'2025-04-20'},
					{money:'215.89',arrMoney:'本金0.00 利息 215.89',data:'2025-03-20'},
					{money:'215.89',arrMoney:'本金0.00 利息 215.89',data:'2025-02-20'},
					{money:'215.89',arrMoney:'本金0.00 利息 215.89',data:'2025-01-20'},
					{money:'42,185,15',arrMoney:'本金0.00 利息 42,185,15',data:'2024-12-20'},
					{money:'43,989,32',arrMoney:'本金0.00 利息 43,989,32',data:'2024-11-20'},
					{money:'45,260,42',arrMoney:'本金0.00 利息 45,260,42',data:'2024-10-20'},
					{money:'46,769.10',arrMoney:'本金0.00 利息 46,769.10',data:'2024-09-20'},
					{money:'46,883.68',arrMoney:'本金0.00 利息 46,883.68',data:'2024-08-20'},
					{money:'96,575,50',arrMoney:'本金500,000.00 利息 46,575,50',data:'2024-07-20'},
					{money:'48,127.50',arrMoney:'本金0.00 利息 48,127.50',data:'2024-06-20'},
					{money:'46,575.00',arrMoney:'本金0.00 利息 46,575.00',data:'2024-05-20'},
					{money:'48,127.50',arrMoney:'本金0.00 利息 48,127.50',data:'2024-04-20'},
					{money:'45,022.50',arrMoney:'本金0.00 利息 45,022.50',data:'2024-03-20'},
					{money:'48,127.50',arrMoney:'本金0.00 利息 48,127.50',data:'2024-02-20'},
					{money:'98,301.88',arrMoney:'本金500,000.00 利息 48,301.88',data:'2024-01-20'},
					{money:'46,743.75',arrMoney:'本金0.00 利息 46,743.75',data:'2023-12-20'},
					{money:'48,301.88',arrMoney:'本金0.00 利息 48,301.88',data:'2023-11-20'},
					{money:'46,743.75',arrMoney:'本金0.00 利息 46,743.75',data:'2023-10-20'},
					{money:'48,378.82',arrMoney:'本金0.00 利息 48,378.82',data:'2023-09-20'},
					{money:'49,494.51',arrMoney:'本金0.00 利息 49,494.51',data:'2023-08-20'},
					{money:'98,109,44',arrMoney:'本金500,000.00 利息 48,109.44',data:'2025-07-20'},
					{money:'50,870.14',arrMoney:'本金0.00 利息 50,870.14',data:'2023-06-20'},
					{money:'49,229.17',arrMoney:'本金0.00 利息 49,229.17',data:'2023-05-20'},
					{money:'54,866.39',arrMoney:'本金0.00 利息 54,866.39',data:'2023-04-20'},
					{money:'50,812,22',arrMoney:'本金0.00 利息 50,812,22',data:'2023-03-20'},
					{money:'56,256.39',arrMoney:'本金0.00 利息 56,256.39',data:'2023-02-20'},
					{money:'156,661.11',arrMoney:'本金100,000.00 利息 56,661.11',data:'2023-01-20'},
					{money:'54,833.33',arrMoney:'本金0.00 利息 54,833.33',data:'2022-12-20'},
					{money:'56,661.11',arrMoney:'本金0.00 利息 56,661.11',data:'2025-11-20'},
					{money:'54,833.33',arrMoney:'本金0.00 利息 54,833.33',data:'2022-10-20'},
					{money:'56,661.11',arrMoney:'本金0.00 利息 56,661.11',data:'2022-09-20'},
					{money:'43,866.67',arrMoney:'本金0.00 利息 43,866.67',data:'2022-08-20'},
				]
			};
		}
	}
</script>

<style lang="scss">
	.datali{
		padding: 20rpx;
		background-color: #fff;
		margin-top: 10rpx;
		p{
			font-size: 25rpx;
			color: #888;
		}
		.list-datali{
			padding: 30rpx 0;
			display: flex;
			justify-content: space-between;
			.datali-money{
				display: flex;
				flex-wrap: wrap;
				margin-top: 20rpx;
				span{
					font-size: 32rpx;
				}
				text{
					width: 100%;
					font-size: 25rpx;
					color: #888;
					margin-top: 10rpx;
				}
			}
			.text{
				width: 25%;
				display: flex;
				align-items: self-end;
				justify-content: center;
				color: #888;
				font-size: 25rpx;
			}
		}
	}
</style>