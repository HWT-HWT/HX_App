<template>
	<view class="IncomeExpenses">
		<view>
			<view class="title">
				<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
				<view class="title-taber">
					<view class="taber" v-for="(item,index) in titleTaber" :key="index" @click="TbaIndex(index)">
						<text :style="{fontWeight:index === tabIndex ? 'bold' : 'normal'}">{{item}}</text>
						<view class="box" :style="{opacity:index === tabIndex ? '1' : '0'}"></view>
					</view>
				</view>
				<view class="right-icon">
					<view class="icon">
						<image src="@/static/server-1.png" mode=""></image>
					</view>
					<view class="icon">
						<image src="@/static/server-2.png" mode=""></image>
					</view>
				</view>
			</view>
			<view class="taber">
				<view class="tb" v-for="(item,index) in taber" :key="index" @click="getIndex(index)">
					<span v-if="index == 0">{{cardName || item}}</span>
					<span v-if="index == 1">{{date || item}}</span>
					<span v-if="index == 2">{{select || item}}</span>
					<image src="../../static/recording-1.png" mode="" v-if="index !== 2"></image>
				</view>
			</view>
		</view>
		
		<view class="position" v-if="TopScroll > 25">
			<view class="title">
				<image class="left" src="@/static/left-cion-1.png" mode="" @click="back"></image>
				<view class="title-taber">
					<view class="taber" v-for="(item,index) in titleTaber" :key="index" @click="TbaIndex(index)">
						<text :style="{fontWeight:index === tabIndex ? 'bold' : 'normal'}">{{item}}</text>
						<view class="box" :style="{opacity:index === tabIndex ? '1' : '0'}"></view>
					</view>
				</view>
				<view class="right-icon">
					<view class="icon">
						<image src="@/static/server-1.png" mode=""></image>
					</view>
					<view class="icon">
						<image src="@/static/server-2.png" mode=""></image>
					</view>
				</view>
			</view>
			<view class="taber">
				<view class="tb" v-for="(item,index) in taber" :key="index" @click="getIndex(index)">
					<span v-if="index == 0">{{cardName || item}}</span>
					<span v-if="index == 1">{{date || item}}</span>
					<span v-if="index == 2">{{select || item}}</span>
					<image src="../../static/recording-1.png" mode="" v-if="index !== 2"></image>
				</view>
			</view>
			<view class="listTitle" v-for="(item,index) in TopScrollList" :key="index">
				<view class="yesr">
					<text>{{item.Month}}</text>
					<view class="span">
						<span>{{item.Year}}</span>
					</view>
				</view>
				<view class="text-icon">
					<span>月账单</span>
					<image src="../../static/upsdk_payment_right.webp" mode=""></image>
				</view>
				<span class="subTitle">{{item.money}}</span>
			</view>
		</view>
		
		<IncomeExpensesTaberVue :selectIndex='selectIndex' @btn='btn' @data='data'></IncomeExpensesTaberVue>
		
		<view v-if="tabIndex == 0">
			<view class="IncomeExpenses-list" v-for="(item,index) in list" :key="index">
				<view class="listTitle">
					<view class="yesr">
						<text>{{item.Month}}</text>
						<view class="span">
							<span>{{item.Year}}</span>
						</view>
					</view>
					<view class="text-icon">
						<span>月账单</span>
						<image src="../../static/upsdk_payment_right.webp" mode=""></image>
					</view>
				</view>
				<span class="subTitle">{{item.money}}</span>
				<view class="list">
					<view class="li" v-for="(sum,num) in item.date" :key="num">
						<view class="date">
							<image src="../../static/index-icon-1.png" mode=""></image>
						</view>
						<view class="centent">
							<view class="centent-view">
								<view class="Left-View">
									<span>{{sum.title}}</span>
									<p>余额 {{sum.balance}}</p>
								</view>
								<view class="Right-View">
									<p> <text :style="{color: sum.color ? '#d8111c':'#000'}">{{sum.add}}</text></p>
									<view>华夏卡 {{sum.username}}</view>
								</view>
							</view>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="month" v-if="tabIndex == 1">
			<view class="month-box">
				<view class="box">
					<span>支出</span>
					<text>0.00</text>
				</view>
				<view class="box" style="background: #fff; color: #be9e67;" >
					<span>支出</span>
					<text>0.00</text>
				</view>
			</view>
			<view class="SubTitme">
				本月入不敷出,要注意节流开支奥~
			</view>
			<image src="@/static/IncomeExpenses-bg-1.png" mode=""></image>
		</view>
	</view>
	
</template>

<script>
	import IncomeExpensesTaberVue from '../../components/IncomeExpenses-taber.vue';
	export default {
		data() {
			return {
				titleTaber:['我的账户','月账单'],
				taber:['银行卡','2025-08','筛选'],
				tabIndex:0,
				TopScroll:0,
				TopScrollList:[
					{
						Year:'2025年',
						Month:'8月',
						money:'支出￥12,400.13 收入￥0.00',
					},
				],
				list:[
					{
						Year:'2025年',
						Month:'8月',
						money:'支出￥12,400.13 收入￥0.00',
						date:[
							{Day:'01',title:'贷款-扣收贷本息',balance:'08-20 周三 02:01',username:'￥33,579.98',add:'-12,400.13',color:false},
						],
					},
					{
						Year:'2025年',
						Month:'7月',
						money:'支出￥62,467.53 收入￥0.00',
						date:[
							{Day:'01',title:'贷款-扣收贷本息',balance:'07-20 周日 02:32',username:'46,160.11',add:'-62,467.53',color:false},
						],
					},
					{
						Year:'2025年',
						Month:'6月',
						money:'支出￥84,833.08 收入￥0.17',
						date:[
							{Day:'01',title:'结息',balance:'06-20 周五 00:32',username:'108,627.64',add:'+0.17',color:true},
							{Day:'01',title:'贷款-扣收贷本息',balance:'06-20 周五 02:08',username:'108,627.47',add:'-12,155.75',color:false},
							{Day:'01',title:'跨行收款-吴志斐',balance:'06-02 周一 23:59',username:'121,083.22',add:'+300.00',color:true},
							{Day:'01',title:'跨行收款-吴志斐',balance:'06-02 周一 23:57',username:'120,783.22.',add:'+30.000.00',color:true},
							{Day:'01',title:'跨行收款-吴志斐',balance:'06-02 周一 23:16',username:'90,783.22',add:'+13,300.00',color:true},
						],
					},
					{
						Year:'2025年',
						Month:'5月',
						money:'支出￥12,094.36 收入￥0.00',
						date:[
							{Day:'01',title:'贷款-扣收贷本息',balance:'05-20 周二 02:12',username:'77,483.22',add:'-12,094.36',color:false},
						],
					},
					{
						Year:'2025年',
						Month:'4月',
						money:'支出￥1,066,449.72 收入￥958,071.00',
						date:[
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-23 周三 23:11',username:'89,577.58',add:'-6,000.00',color:false},
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-22 周二 23:09',username:'85,577.58',add:'+6,000.00',color:true},
							{Day:'01',title:'手机银行转出-唐曼',balance:'04-22 周二 23:03',username:'89,577.58',add:'-30,000.00',color:false},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-22 周二 23:01',username:'119,577.58',add:'-220,000.00',color:false},
							{Day:'01',title:'人行跨行收款-段银飞',balance:'04-22 周二 22:10',username:'339,577.58',add:'+150,000.00',color:true},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-22 周二 22:02',username:'189,577.58',add:'-38,000.00',color:false},
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-22 周二 21:19',username:'227,577.58',add:'+6,000.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-22 周二 21:03',username:'221,577.58',add:'-200,000.00',color:false},
							{Day:'01',title:'人行跨行收款-颜勇',balance:'04-22 周二 20:59',username:'421,577.58',add:'+150,000.00',color:true},
							{Day:'01',title:'银联跨行取款',balance:'04-22 周二 16:30',username:'271,577.58',add:'-5,000.00',color:false},
							{Day:'01',title:'银联跨行取款',balance:'04-22 周二 16:27',username:'276,577.58',add:'-5,000.00',color:false},
							{Day:'01',title:'银联跨行取款',balance:'04-22 周二 16:24',username:'281,577.58',add:'-5,000.00',color:false},
							{Day:'01',title:'银联跨行取款',balance:'04-22 周二 16:20',username:'286,577.58',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-20 周日 16:11',username:'291,577.58',add:'+20,000.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-20 周日 15:50',username:'271,577.58',add:'-10,500.00',color:false},
							{Day:'01',title:'人行跨行收款-翟伟斌',balance:'04-20 周日 15:39',username:'282,077.58',add:'+10,000.00',color:true},
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-20 周日 15:25',username:'282,077.58',add:'+30,600.00',color:true},
							{Day:'01',title:'贷款-扣收贷本息-吴志斐',balance:'04-20 周日 15:12',username:'241,477.58',add:'-12,471.31',color:false},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-20 周日 15:50',username:'253,938.89',add:'-20,000.00',color:false},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-20 周日 15:42',username:'272,077.89',add:'-33,000.00',color:false},
							{Day:'01',title:'手机银行转出-吴志斐',balance:'04-20 周日 15:32',username:'241,477.89',add:'-10,000.00',color:false},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-20 周日 15:20',username:'253,948.89',add:'-5,000.00',color:false},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-20 周日 14:39',username:'273,948.89',add:'-4,000.00',color:false},
							{Day:'01',title:'手机银行转出-戴利川',balance:'04-20 周日 14:30',username:'306,948.89',add:'-20,100.00',color:false},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-19 周六 12:02',username:'316,948.89',add:'-50,000.00',color:false},
							{Day:'01',title:'人行跨行收款-段银飞',balance:'04-19 周六 10:19',username:'395,048.89',add:'+150,000.00',color:true},
							{Day:'01',title:'手机银行转出-吴志斐',balance:'04-19 周六 10:11',username:'246,048.89',add:'-50,000.00',color:false},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-19 周六 09:02',username:'251,048.89',add:'-4,000.00',color:false},
							{Day:'01',title:'手机银行转出-秦信龙',balance:'04-19 周六 08:10',username:'255,048.89',add:'-20,100.00',color:false},
							{Day:'01',title:'手机银行转出-姚荣志',balance:'04-19 周六 00:30',username:'275,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-秦信龙',balance:'04-19 周六 00:20',username:'325,276.89',add:'+150,000.00',color:true},
							{Day:'01',title:'手机银行转出-姚荣志',balance:'04-19 周六 00:05',username:'175,276.89',add:'-12,128.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-18 周五 10:53',username:'187,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-18 周五 10:50',username:'192,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-18 周五 10:45',username:'197,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-18 周五 10:35',username:'2022,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-18 周五 02:32',username:'207,276.89',add:'+20,000.00',color:true},
							{Day:'01',title:'手机银行转出-杨涛',balance:'04-18 周五 01:25',username:'187,276.89',add:'-15,000.00',color:false},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-18 周五 00:32',username:'202,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-18 周五 00:20',username:'207,276.89',add:'+5,000.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-17 周四 15:50',username:'204,276.89',add:'-50,000.00',color:false},
							{Day:'01',title:'手机银行转出-刘志源',balance:'04-17 周四 15:45',username:'254,276.89',add:'-13,000.00',color:false},
							{Day:'01',title:'手机银行转出-邓学琛',balance:'04-17 周四 15:43',username:'267,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-刘志源',balance:'04-17 周四 15:40',username:'272,276.89',add:'+10,000.00',color:true},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-17 周四 14:32',username:'172,276.89',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-17 周四 14:30',username:'177,276.89',add:'+5,000.00',color:true},
							{Day:'01',title:'手机银行转出-叶柳机',balance:'04-16 周三 09:52',username:'172,276.89',add:'-2,250.00',color:false},
							{Day:'01',title:'手机银行转出-邓学琛',balance:'04-16 周三 09:46',username:'174,526.89',add:'-2,000.00',color:false},
							{Day:'01',title:'手机银行转出-秦鑫',balance:'04-16 周三 09:32',username:'176,526.89',add:'-3,000.00',color:false},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-16 周三 09:20',username:'179,526.89',add:'-2,500.00',color:false},
							{Day:'01',title:'人行跨行收款-张燕玲',balance:'04-16 周三 00:42',username:'182,026.89',add:'+10,000.00',color:true},
							{Day:'01',title:'手机银行转出-乐明凤',balance:'04-16 周三 00:32',username:'172,026.89',add:'-4,000.00',color:false},
							{Day:'01',title:'人行跨行收款-陈文明',balance:'04-16 周三 00:30',username:'176,026.89',add:'+4,000.00',color:true},
							{Day:'01',title:'手机银行转出-卢庆棠',balance:'04-16 周三 00:24',username:'172,026.89',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-张燕玲',balance:'04-16 周三 00:12',username:'177,026.89',add:'+5,000.00',color:true},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-15 周二 14:27',username:'172,026.89',add:'-2,500.00',color:false},
							
							{Day:'01',title:'人行跨行收款-杨阳',balance:'04-15 周二 14:12',username:'174,526.89',add:'+3,000.00',color:true},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-12 周六 09:52',username:'171,526.89',add:'-40,200.00',color:false},
							{Day:'01',title:'手机银行转出-张鑫',balance:'04-12 周六 09:46',username:'211,726.89',add:'-7,000.00',color:false},
							{Day:'01',title:'人行跨行收款-张燕玲',balance:'04-12 周六 14:12',username:'218,726.89',add:'+47,200.00',color:true},
							{Day:'01',title:'手机银行转出-劳朝莲',balance:'04-12 周六 09:52',username:'171,576.89',add:'-24,063.00',color:false},
							{Day:'01',title:'人行跨行收款-张燕玲',balance:'04-12 周六 14:12',username:'195,589.89',add:'+23,971.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-12 周六 09:52',username:'171,618.89',add:'-1,500.00',color:false},
							{Day:'01',title:'手机银行转出-劳朝莲',balance:'04-12 周六 09:52',username:'173,118.89',add:'-24,000.00',color:false},
							{Day:'01',title:'人行跨行收款-张燕玲',balance:'04-12 周六 14:12',username:'197,118.89',add:'+22,000.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-12 周六 09:52',username:'175,118.89',add:'-3,000.00',color:false},
							{Day:'01',title:'手机银行转出-乐明凤',balance:'04-12 周六 09:52',username:'178,118.89',add:'-5,000.00',color:false},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-12 周六 09:52',username:'183,118.89',add:'-30,000.00',color:false},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'04-12 周六 14:12',username:'213,118.89',add:'+40,000.00',color:true},
							{Day:'01',title:'手机银行转出-吴志斐',balance:'04-12 周六 09:52',username:'173,118.89',add:'-18,900.00',color:false},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-12 周六 09:52',username:'192,018.89',add:'-3,500.00',color:false},
							{Day:'01',title:'手机银行转出-卢庆棠',balance:'04-12 周六 09:52',username:'195,518.89',add:'-5,000.00',color:false},
							{Day:'01',title:'手机银行转出-曾立娟',balance:'04-12 周六 09:52',username:'200,518.89',add:'-6,000.00',color:false},
							{Day:'01',title:'手机银行转出-李普',balance:'04-12 周六 09:52',username:'206,518.89',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'04-12 周六 14:12',username:'211,518.89',add:'+40,000.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-10 周四 09:52',username:'171,518.89',add:'-14,900.00',color:false},
							{Day:'01',title:'手机银行转出-袁信亮',balance:'04-10 周四 09:52',username:'186,418.89',add:'-3,500.00',color:false},
							{Day:'01',title:'手机银行转出-张永钊',balance:'04-10 周四 09:52',username:'189,918.89',add:'-10,000.00',color:false},
							{Day:'01',title:'手机银行转出-叶小用',balance:'04-10 周四 09:52',username:'199,978.89',add:'-5,000.00',color:false},
							{Day:'01',title:'手机银行转出-李普',balance:'04-10 周四 09:52',username:'204,918.89',add:'-5,000.00',color:false},
							
							{Day:'01',title:'手机银行转出-曾立娟',balance:'04-10 周四 09:52',username:'209,918.89',add:'-6,000.00',color:false},
							{Day:'01',title:'手机银行转出-乐明凤',balance:'04-10 周四 09:52',username:'215,987.89',add:'-5,000.00',color:false},
							{Day:'01',title:'手机银行转出-陈雅珍',balance:'04-10 周四 09:52',username:'220,918.89',add:'-10,000.00',color:false},
							{Day:'01',title:'手机银行转出-泰鑫',balance:'04-10 周四 09:52',username:'230,918.89',add:'-8,000.00',color:false},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'04-10 周四 14:12',username:'238,918.89',add:'+67,363.46',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-08 周二 09:52',username:'171,555.43',add:'-40,257.00',color:false},
							{Day:'01',title:'手机银行转账-陈学昌',balance:'04-08 周二 09:52',username:'211,812.43',add:'+40,300.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-06 周日 09:52',username:'171,512.43',add:'-130,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-06 周日 10:53',username:'301,512.43',add:'-5,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-06 周日 10:50',username:'306,512.43',add:'-5,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-06 周日 10:45',username:'311,512.43',add:'-5,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'04-06 周日 10:35',username:'316,512.43',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-曾炎强',balance:'04-06 周日 14:12',username:'321,512.43',add:'+150,000.00',color:true},
							{Day:'01',title:'手机银行转出-杨阳',balance:'04-06 周日 09:52',username:'171,512.43',add:'-102,200.00',color:false},
						],
					},
					{
						Year:'2025年',
						Month:'3月',
						money:'支出￥219,742.41 收入￥160,000.02',
						date:[
							{Day:'01',title:'手机银行转出-吴志斐',balance:'03-29 周六 14:52',username:'273,712.43',add:'-120,000.00',color:false},
							{Day:'01',title:'人行跨行收款-张莹',balance:'03-29 周六 14:48',username:'393,712.43',add:'+150,000.00',color:true},
							{Day:'01',title:'自助设备现金取款',balance:'03-29 周六 14:36',username:'243,712.43',add:'-3,000.00',color:false},
							{Day:'01',title:'自助设备现金取款',balance:'03-29 周六 14:32',username:'246,712.43',add:'-5,000.00',color:false},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'03-29 周六 11:05',username:'251,712.43',add:'+80,000.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'03-29 周六 11:01',username:'171,712.43',add:'+96,500.00',color:true},
							{Day:'01',title:'银联银联入账-吴志斐',balance:'03-25 周二 11:52',username:'75,212.43',add:'+100,000.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'03-24 周一 09:40',username:'75,212.43',add:'+500.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'03-23 周日 10:32',username:'64,712.43',add:'+800.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'03-22 周六 09:10',username:'63,912.43',add:'+2,000.00',color:true},
							{Day:'01',title:'贷款-扣收贷本息',balance:'03-21 周五 10:32',username:'61,912.43',add:'-11,936.00',color:false},
							{Day:'01',title:'存款结息',balance:'03-21 周五 09:10',username:'73,848.43',add:'+0.02',color:true},
						],
					},
					{
						Year:'2025年',
						Month:'2月',
						money:'支出￥32,000.00 收入￥32,000.00',
						date:[
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-20 周四 14:48',username:'73,848.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-09 周日 09:11',username:'73,548.41',add:'+500.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-08 周日 11:13',username:'73,048.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-07 周五 12:13',username:'72,748.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-06 周四 11:10',username:'72,448.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-05 周三 14:12',username:'72,148.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-04 周二 11:24',username:'71,848.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-03 周一 15:31',username:'71,548.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-02 周日 14:12',username:'71,248.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'02-01 周六 11:02',username:'70,948.41',add:'+500.00',color:true},
						],
					},
					{
						Year:'2025年',
						Month:'1月',
						money:'支出￥12,094.36 收入￥0.00',
						date:[
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-31 周五 14:48',username:'73,048.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-31 周五 14:39',username:'72,748.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-30 周四 11:36',username:'72,448.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-29 周三 10:32',username:'72,148.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-28 周二 09:48',username:'71,848.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-27 周一 09:30',username:'71,548.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-26 周日 10:32',username:'71,248.41',add:'+300.00',color:true},
							{Day:'01',title:'人行跨行收款-吴志斐',balance:'01-20 周一 12:12',username:'62,517.41',add:'-500.00',color:false},
						],
					},
					
				],
				selectIndex:999,
				cardName:'银行卡',
				date:'2025-08',
				select:'筛选'
			};
		},
		methods:{
			TbaIndex(index){
				this.tabIndex = index
			},
			back(){
				uni.navigateBack()
			},
			getIndex(index){
				this.selectIndex = index
			},
			btn(res){
				var index = res[1]
				this.cardName = res[0][index]
				this.selectIndex = 999
			},
			data(res){
				this.date = res,
				this.selectIndex = 999
			}
		},
		components:{
			IncomeExpensesTaberVue
		},
		onPageScroll(top) {
			this.TopScroll = top.scrollTop
			console.log(top.scrollTop);
			top.scrollTop > 0 ? this.TopScrollList[0] = this.list[0] : ''
			top.scrollTop > 175 ? this.TopScrollList[0] = this.list[1] : ''
			top.scrollTop > 335 ? this.TopScrollList[0] = this.list[2] : ''
			top.scrollTop > 735 ? this.TopScrollList[0] = this.list[3] : ''
			top.scrollTop > 890 ? this.TopScrollList[0] = this.list[4] : ''
			top.scrollTop > 8350 ? this.TopScrollList[0] = this.list[5] : ''
			top.scrollTop > 9320 ? this.TopScrollList[0] = this.list[6] : ''
		}
	}
</script>

<style lang="scss">
	.IncomeExpenses{
		margin: 0 auto;
		min-height: 100vh;
		background-color: #f5f5f5;
		.title{
			width: 100%;
			margin: 0 auto;
			margin-top: 80rpx;
			padding:30rpx 0;
			background-color: #fff;
			display: flex;
			align-items: center;
			justify-content: space-between;
			text-align: center;
			.left{
				width: 30rpx;
				height: 40rpx;
				padding: 0 20rpx;
			}
			.title-taber{
				display: flex;
				margin-left: 100rpx;
				.taber{
					display: flex;
					flex-wrap: wrap;
					text-align: center;
					justify-content: center;
					text{
						width: 100%;
						font-size: 30rpx;
						font-weight: bold;
					}
					.box{
						width: 35rpx;
						margin-top: 10rpx;
						padding: 4rpx;
						border-radius: 100rpx;
						background-color: #c60127;
					}
				}
			}
			
			.right-icon{
				display: flex;
				padding: 0 20rpx;
				.icon{
					margin-left: 10rpx;
					display: flex;
					align-items: center;
					justify-content: center;
					flex-wrap: wrap;
					text-align: center;
					image{
						width: 50rpx;
						height: 50rpx;
					}
					span{
						width: 100%;
						font-size: 20rpx;
						margin-top: -5rpx;
					}
				}
			}
		}
		.position{
			position: fixed;
			width: 100%;
			z-index: 999;
			top: 0;
			background-color: #fff;
			padding-bottom: 30rpx;
			margin-top: 0;
			.listTitle{
				padding:20rpx 30rpx;
				padding-bottom:0rpx ;
				display: flex;
				flex-wrap: wrap;
				justify-content: space-between;
				text{
					font-size: 40rpx;
					font-weight: bold;
				}
				.yesr{
					display: flex;
					.span{
						display: flex;
						align-items: self-end;
						font-size: 28rpx;
						font-weight: bold;
						margin-left: 10rpx;
					}
				}
				.text-icon{
					display: flex;
					align-items: center;
					color: #6ca1f0;
					image{
						width: 40rpx;
						height: 40rpx;
					}
				}
				.subTitle{
					width: 100%;
					font-size: 24rpx;
					color: #888;
				}
			}
		}
		.taber{
			background-color: #fff;
			padding-bottom: 20rpx;
			display: flex;
			.tb{
				width: 100%;
				display: flex;
				align-items: center;
				justify-content: center;
				span{
					text-align: center;
					
					font-size: 28rpx;
				}
				image{
					width: 25rpx;
					height: 20rpx;
					margin-left: 10rpx;
				}
			}
		}
		.IncomeExpenses-list{
			background-color: #fff;
			margin-top: 20rpx;
			.listTitle{
				padding:20rpx 30rpx;
				padding-bottom:0rpx ;
				display: flex;
				justify-content: space-between;
				text{
					font-size: 40rpx;
					font-weight: bold;
				}
				.yesr{
					display: flex;
					.span{
						display: flex;
						align-items: self-end;
						font-size: 28rpx;
						font-weight: bold;
						margin-left: 10rpx;
					}
				}
				.text-icon{
					display: flex;
					align-items: center;
					color: #6ca1f0;
					image{
						width: 40rpx;
						height: 40rpx;
					}
				}
			}
			.subTitle{
				padding:0 30rpx;
				font-size: 28rpx;
				margin-top: 20rpx;
			}
			.list{
				margin-top: 20rpx;
				background-color: #fff;
				.li{
					padding: 20rpx;
					display: flex;
					border-bottom: 1px solid #f5f5f5;
					align-content: center;
					image{
						width: 60rpx;
						height: 60rpx;
					}
					.date{
						color: #888;
						display: flex;
						flex-wrap: wrap;
						justify-content: center;
						align-items: center;
						view{
							min-width: 40rpx;
							padding: 20rpx;
							span{
								font-size: 35rpx;
								font-weight: bold;
							}
							p{
								text-align: center;
								width: 100%;
								font-size: 18rpx;
							}
						}
						
					}
					.centent{
						flex: 1;
						background-color: #fff;
						display: flex;
						align-items: center;
						.centent-view{
							width: 100%;
							font-size: 25rpx;
							padding: 10rpx;
							display: flex;
							justify-content: space-between;
							.Left-View{
								span{
									font-size: 28rpx;
									
								}
								p{
									padding-top:10rpx ;
									margin-top: 5rpx;
									color: #888;
								}
							}
							.Right-View{
								text-align: right;
								p{
									font-weight: bold;
									margin-top: 5rpx;
									color:#6f6f6f;
									font-size: 30rpx;
									color: #000;
									text{
										padding-left:10rpx;
									}
								}
								view{
									font-size: 25rpx;
									margin-top: 10rpx;
									color: #888;
								}
								
							}
						}
					}
				}
			}
		}
		.month{
			padding: 20rpx 0;
			background-color: #fff;
			.month-box{
				display: flex;
				align-items: center;
				justify-content: center;
				.box{
					background:url('@/static/Transfer-bg-2.png') ;
					background-size:100% 100%;
					margin: 0 10rpx;
					border-radius: 10rpx;
					box-shadow:  0 0 20rpx 1rpx rgba(0, 0, 0, 0.1);
					padding: 10rpx 60rpx;
					display: flex;
					justify-content: center;
					flex-wrap: wrap;
					text-align: center;
					color: #fff;
					font-weight: bold;
					span{
						width: 100%;
					}
				}
			}
			.SubTitme{
				width: 95%;
				text-align: center;
				border-radius: 10rpx;
				margin: 20rpx auto;
				padding: 10rpx 0;
				font-size: 28rpx;
				background-color:#f2f2f2;
			}
			image{
				margin-top: 20rpx;
				width: 100%;
				height: 300rpx;
			}
		}
		
	}
</style>
