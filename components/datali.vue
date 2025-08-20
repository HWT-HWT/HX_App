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
					{money:'12,400.00',arrMoney:'本金0.00 利息 12,400.00',data:'2025-08-20'},
					{money:'62,467.53',arrMoney:'本金50,000.00 利息 12,467.53',data:'2025-07-20'},
					{money:'12,155.75',arrMoney:'本金0.00 利息 12,155.75',data:'2025-06-20'},
					{money:'12,094.36',arrMoney:'本金0.00 利息 12,094.36',data:'2025-05-20'},
					{money:'12,471.31',arrMoney:'本金0.00 利息 12,471.31',data:'2025-04-20'},
					{money:'11,936.00',arrMoney:'本金0.00 利息 11,936.00',data:'2025-03-21'},
					{money:'12,471.31',arrMoney:'本金0.00 利息 12,471.31',data:'2025-02-20'},
					{money:'62,571.35',arrMoney:'本金50,000.00 利息 12,571.35',data:'2025-01-20'},
					{money:'12,113.05',arrMoney:'本金0.00 利息 12,113.05',data:'2024-12-20'},
					{money:'12,571.14',arrMoney:'本金0.00 利息 12,571.14',data:'2024-11-20'},
					{money:'12,931.52',arrMoney:'本金0.00 利息 12,931.52',data:'2024-10-20'},
					{money:'13,362.10',arrMoney:'本金0.00 利息 13,362.10',data:'2024-09-20'},
					{money:'13,395.39',arrMoney:'本金0.00 利息 13,395.39',data:'2024-08-20'},
					{money:'63,307.14',arrMoney:'本金50,000.00 利息 13,307.14',data:'2024-07-20'},
					{money:'13,750.71',arrMoney:'本金0.00 利息 13,750.71',data:'2024-06-20'},
					{money:'13,307.14',arrMoney:'本金0.00 利息 13,307.14',data:'2024-05-20'},
					{money:'13,750.71',arrMoney:'本金0.00 利息 13,750.71',data:'2024-04-20'},
					{money:'12,863.57',arrMoney:'本金0.00 利息 12,863.57',data:'2024-03-20'},
					{money:'13,750.71',arrMoney:'本金0.00 利息 13,750.71',data:'2024-02-20'},
					{money:'63,800.53',arrMoney:'本金50,000.00 利息 13,800.53',data:'2024-01-20'},
					{money:'13,355.35',arrMoney:'本金0.00 利息 13,355.35',data:'2023-12-20'},
					{money:'13,800.53',arrMoney:'本金0.00 利息 13,800.53',data:'2023-11-20'},
					{money:'13,355.35',arrMoney:'本金0.00 利息 13,355.35',data:'2023-10-20'},
					{money:'13,822.52',arrMoney:'本金0.00 利息 13,822.52',data:'2023-09-20'},
					{money:'14,141.28',arrMoney:'本金0.00 利息 14,141.28',data:'2023-08-20'},
					{money:'63,745.55',arrMoney:'本金50,000.00 利息 13,745.55',data:'2025-07-20'},
					{money:'14,534.32',arrMoney:'本金0.00 利息 14,534.32',data:'2023-06-20'},
					{money:'14,065.51',arrMoney:'本金0.00 利息 14,065.51',data:'2023-05-20'},
					{money:'15,676.11',arrMoney:'本金0.00 利息 15,676.11',data:'2023-04-20'},
					{money:'14,517.77',arrMoney:'本金0.00 利息 14,517.77',data:'2023-03-20'},
					{money:'16,073.25',arrMoney:'本金0.00 利息 16,073.25',data:'2023-02-20'},
					{money:'116,188.88',arrMoney:'本金100,000.00 利息 16,188.88',data:'2023-01-20'},
					{money:'15,666.66',arrMoney:'本金0.00 利息 15,666.66',data:'2022-12-20'},
					{money:'16,188.88',arrMoney:'本金0.00 利息 16,188.88',data:'2025-11-20'},
					{money:'15,666.66',arrMoney:'本金0.00 利息 15,666.66',data:'2022-10-20'},
					{money:'16,188.88',arrMoney:'本金0.00 利息 16,188.88',data:'2022-09-20'},
					{money:'12,533.33',arrMoney:'本金0.00 利息 12,533.33',data:'2022-08-20'},
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