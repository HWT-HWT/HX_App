<template>
	<view class="SelectData">
		<view class="popup-content" :class="{ 'popup-height': type === 'left' || type === 'right' }">
			<picker-view v-if="visible" :indicator-style="indicatorStyle" :value="valueData" @change="bindChange" class="picker-view">
				<picker-view-column>
					<view class="item" v-for="(item,index) in years" :key="index">{{item}}年</view>
				</picker-view-column>
				<picker-view-column>
					<view class="item" v-for="(item,index) in months" :key="index">{{item}}月</view>
				</picker-view-column>
			   <picker-view-column v-if="dataTrue == 1 ">
					<view class="item" v-for="(item,index) in days" :key="index">{{item}}日</view>
				</picker-view-column>
			</picker-view>
		</view>
		<view class="btnList">
			<view class="btn">
				重置
			</view>
			<view class="btn" @click="right" style="background-color: #e8182d; color: #fff;">
				确定
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data: function () {
			const date = new Date()
			const years = []
			const year = date.getFullYear()
			const months = []
			const month = date.getMonth() + 1
			const days = []
			const day = date.getDate()
			for (let i = 1990; i <= date.getFullYear(); i++) {
				years.push(i)
			}
			for (let i = 1; i <= 12; i++) {
				months.push(i)
			}
			for (let i = 1; i <= 31; i++) {
				days.push(i)
			}
			return {
				years,
				year,
				months,
				month,
				days,
				day,
				valueData: [9999, month - 1, day - 1],
				visible: true,
				indicatorStyle: `height: 50px;`,
				type: 'center',
				msgType: 'success',
				messageText: '这是一条成功提示',
				value: '',
				current:0
			}
		},
		methods: {
			bindChange: function (e) {
				const val = e.detail.value
				this.year = this.years[val[0]]
				this.month = this.months[val[1]]
				this.day = this.days[val[2]]
			},
			// 检测时间选择器状态 打开为 true 关闭 false
			change(e) {
				console.log('当前模式：' + e.type + ',状态：' + e.show);
			},
			tabsChange(index){
				this.current = index
			},
			right(){
				// console.log(this.year,this.month);
				this.$emit('change',[this.year,this.month])
			},
		},
		props:{
				StartedEnd:{
					type:Number
				},
				dataTrue:{
					type:Number,
					default:0
				}
		},
		components:{
			
		},
	}
</script>

<style lang="scss" scoped>
	.SelectData{
		background-color: #fff;
		height: 1200rpx;
	}
	.picker-view {
		width: 750rpx;
		height: 600rpx;
	}
	.item {
		line-height: 100rpx;
		text-align: center;
	}
	.popup-Top-Btn{
		padding: 20rpx;
		font-size: 28rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		span{
			color: dodgerblue;
		}
	}
	.btnList{
		display: flex;
		justify-content: space-evenly;
		margin-top: 400rpx;
		.btn{
			padding: 20rpx 120rpx;
			border: 1px solid #db0e1c;
			color:#db0e1c;
			border-radius: 50rpx;
		}
	}
</style>