<template>
	<view class="load">
		<loadOneVue v-if="TaberIndex==0"></loadOneVue>
		<loadTwoVue v-if="TaberIndex==1"></loadTwoVue>
		<loadTherrVue v-if="TaberIndex==2"></loadTherrVue>
		<view class="load-Tab">
			<view class="taber" v-for="(item,index) in tabers" :key="index" @click="SetIndex(index)">
				<image :src="item.selectIcon" mode="" v-if="index == TaberIndex"></image>
				<image :src="item.icon" mode="" v-else ></image>
				<text>{{item.text}}</text>
			</view>
		</view>
	</view>
</template>

<script>
	import loadOneVue from '../../components/load-one.vue';
	import loadTwoVue from '../../components/load-two.vue';
	import loadTherrVue from '../../components/load-therr.vue';
	export default {
		data() {
			return {
				tabers:[
					{text:'我要消费',icon:'../../static/load-icon-1.png',selectIcon:'../../static/load-icon-select-1.png'},
					{text:'我要经营',icon:'../../static/load-icon-2.png',selectIcon:'../../static/load-icon-select-2.png'},
					{text:'我的贷款',icon:'../../static/load-icon-3.png',selectIcon:'../../static/load-icon-select-3.png'},
				],
				TaberIndex:0
			};
		},
		methods:{
			SetIndex(index){
				console.log(index);
				this.TaberIndex = index
			}
		},
		onLoad(url) {
			this.TaberIndex = url.id || 0
		},
		components:{
			loadOneVue,
			loadTwoVue,
			loadTherrVue
		}
	}
</script>

<style lang="scss" scoped>
	.load{
		width: 100vw;
		min-height: 100vh;
		padding-bottom: 150rpx;
		background-color: #f5f5f5;
		.load-Tab{
			width: 100%;
			background:#fff;
			position: fixed;
			display: flex;
			bottom: 0;
			.taber{
				padding: 20rpx;
				width: 30%;
				display: flex;
				flex-wrap: wrap;
				justify-content: center;
				text-align: center;
				image{
					width: 40rpx;
					height: 40rpx;
				}
				text{
					font-size: 25rpx;
					margin-top: 10rpx;
					width: 100%;
				}
			}
		}
	}
</style>
