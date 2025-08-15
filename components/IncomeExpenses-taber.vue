<template>
	<view class="IncomeExpenses-taber">
		<view class="selectOne index" v-if="selectIndex == 0" >
			<view class="select" v-for="(item,index) in selectOne" :key="index" @click="One(index)">
				<span>{{item}}</span>
				<image src="../static/select-icon-1.png" mode="" :style="{opacity: iconIndexOne == index ? '1': '0'}"></image>
			</view>
		</view>
		<view class="selectTwo index" v-if="selectIndex == 1">
			<view class="select" v-for="(item,index) in selectTwo" :key="index" @click="Tow(index)">
				<span>{{item}}</span>
				<image src="../static/select-icon-1.png" mode="" :style="{opacity: iconIndexTow == index ? '1': '0'}"></image>
			</view>
			<selectData :dataTrue='iconIndexTow'  @change='change'></selectData>
		</view>
	</view>
</template>

<script>
	import selectData from '../components/SelectData.vue'
	export default {
		name:"IncomeExpenses-taber",
		data() {
			return {
				selectOne:['全部','华夏卡(尾号9323)'],
				selectTwo:['按月选择','自定义日期'],
				iconIndexOne:0,
				iconIndexTow:0,
				data:''
			};
		},
		components:{
			selectData
		},
		props:{
			selectIndex:{
				type:Number,
				default:99
				
			}
		},
		methods:{
			One(index){
				this.iconIndexOne = index
				this.$emit('btn',[this.selectOne,this.iconIndexOne])
			},
			Tow(index){
				this.iconIndexTow = index
			},
			change(data){
				this.data = data[0] + '年' + data[1] + '月'
				this.$emit('data',this.data)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.IncomeExpenses-taber{
		.index{
			width: 100vw;
			height: 90vh;
			opacity:1;
			background-color: rgba(0, 0, 0, 0.2);
			position: absolute;
			z-index: 999;
			.select{
				background-color: #fff;
				display: flex;
				justify-content: center;
				border-bottom: 1px solid #e2e2e2;
				padding:30rpx 20rpx;
				align-items: center;
				span{
					font-size: 32rpx;
				}
				image{
					width: 40rpx;
					margin: 0 20rpx;
					height: 40rpx;
				}
			}
		}
	}
</style>