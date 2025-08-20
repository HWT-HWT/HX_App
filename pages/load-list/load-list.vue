<template>
	<view class="load-list">
		<view class="datali-title">
			<loadTitleVue title="提款信息"  textColor="#b48636" :icon="false" titleFW='normal'></loadTitleVue>
		</view>
		<view class="list" v-for="(item,index) in list" :key="index">
			<p>{{item.name}}</p>
			<view class="textView" v-for="(sum,num) in item.li" :key="num">
				<view class="text">{{sum.liName}}</view>
				<view class="span">{{sum.subName}}</view>
			</view>
		</view>
	</view>
</template>

<script>
	import loadTitleVue from '../../components/load-title.vue';
	export default {
		data() {
			return {
				list:[
					{
						name:'基本信息',li:[
							{liName:'产品名称',subName:'个人经营性贷款'},
							{liName:'获批额度',subName:'￥4,000,000.00'},
							{liName:'提款金额',subName:'￥4,000,000.00'},
							{liName:'额度获批日期',subName:'2022-06-24'},
							{liName:'提款日期',subName:'2022-07-27'},
							{liName:'贷款支付方式',subName:'受托支付'},
							{liName:'贷款用途',subName:'其他'},
							{liName:'贷款合同编号',subName:'GZZX29S12020220062 '},
							{liName:'贷款账号',subName:'28650000000002530'},
						],
					},
					{
						name:'期限详情',li:[
							{liName:'贷款期限',subName:'59个月'},
							{liName:'贷款到期日',subName:'2027-06-27'},
							{liName:'贷款剩余期数',subName:'0022期'},
						],
					},
					{
						name:'利率详情',li:[
							{liName:'年利率（单利）',subName:'3.6000%'},
							{liName:'定价基准',subName:'贷款市场报价利率'},
							{liName:'利率加减点数',subName:'+60基点'},
							{liName:'利率调整频率',subName:'立即生效'},
						],
					},
					{
						name:'还款设定',li:[
							{liName:'还款方式',subName:'到期一次性本利清'},
							{liName:'还款卡',subName:'6230 **** **** 9323'},
						],
					}
				]
			};
		},
		components:{
			loadTitleVue
		}
	}
</script>

<style lang="scss">
	.load-list{
		width: 100vw;
		min-height: 100vh;
		background-color: #f2f2f2;
		.datali-title{
			background-color: #fff;
		}
		.list{
			background-color: #fff;
			margin-top: 20rpx;
			
			p{
				width: 98%;
				margin-left: 20rpx;
				border-bottom: 1px solid #ddd;
				padding: 20rpx 0;
				font-size: 35rpx;
			}
			.textView{
				padding: 40rpx 20rpx;
				display: flex;
				font-size: 30rpx;
				.text{
					width: 40%;
				}
				.span{
					flex:1;
				}
			}
		}
	}
</style>
