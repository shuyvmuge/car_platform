<template>
	<view class="page_car">
		<u-notice-bar :text="message" mode="closable" bgColor="#208eff" color="#ffffff"></u-notice-bar>
		<view class="page_car_header">
			<view class="header_content">
				<view class="left">
					<text class="title">功能全览</text>
					<text class="sub_title">高效管理、精准拓客、数字化经营</text>
					<text class="btn">使用教程</text>
				</view>
				<view>
					<image src="/static/imgs/right.png" style="width: 131px;height: 122px;"></image>
				</view>
			</view>
		</view>
		<view class="page_content">
			<view class="menu">
				<template v-for="(item,index) in menus">
					<view class="item" :key="'menu_'+index">
						<view  class="img_view" :style="{background: item.bg}">
							<image :src="item.icon" class="image"></image>
						</view>
						<text class="txt">{{item.txt}}</text>
					</view>
				</template>
			</view>
			<view class="s_menu">
				<template v-for="(item,index) in second_menus">
					<view class="item" :key="'s_menu_'+index">
						<navigator hover-class="path-hover" :url="item.path" class="path">
							<image :src="item.icon" class="image"></image>
							<text class="txt">{{item.txt}}</text>
						</navigator>
					</view>
				</template>
			</view>
		</view>
		
		<car-group :title="CustomerData.title" mode="card">
			<car-grid-board :list="CustomerData.itemList"></car-grid-board>
		</car-group>
	
		<car-group :title="BusinessData.title" :setText="BusinessData.setText" mode="card">
			<car-grid-board :list="BusinessData.itemList"></car-grid-board>
		</car-group>
	</view>
</template>
 
<script>
	export default {
		data() {
			return {
				message: '港股市场因圣诞假期，将于24-25日休市',
				CustomerData: {
					title:'客户运营',
					itemList:[
						{
							id:1,
							title:'保养到期',
							num:9,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:2,
							title:'保险到期',
							num:2,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:3,
							title:'回访',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:4,
							title:'预约',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:5,
							title:'流失预警',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:6,
							title:'流失预警',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:7,
							title:'流失预警',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:8,
							title:'流失预警',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:9,
							title:'流失预警',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:10,
							title:'流失预警',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						},
						{
							id:11,
							title:'流失预警',
							num:19,
							extra:{
								text:'今日+',
								num:6
							}
						}
					]
				},
				BusinessData:{
					title:'经营看板',
					setText:'今天',
					itemList:[
						{
							id:1,
							title:'机修',
							num:9
						},
						{
							id:2,
							title:'美容',
							num:2
						},
						{
							id:3,
							title:'回访',
							num:19
						},
						{
							id:4,
							title:'预约',
							num:19
						},
						{
							id:5,
							title:'洗车',
							num:19
						},
						{
							id:6,
							title:'微信订单',
							num:19
						},
						{
							id:7,
							title:'开卡',
							num:19
						},
						{
							id:8,
							title:'流失预警',
							num:190002
						},
						{
							id:9,
							title:'流失预警',
							num:19,
						},
						{
							id:10,
							title:'流失预警',
							num:19
						},
						{
							id:11,
							title:'流失预警',
							num:19
						}
					]
				},
				menus: [{
						bg: 'linear-gradient(0deg,rgba(9,216,162,1),rgba(90,242,217,1))',
						icon: '/static/imgs/graduation.png',
						txt: '客户档案',
						isFree: true
					},
					{
						bg: 'linear-gradient(0deg,rgba(251,184,35,1),rgba(255,228,40,1))',
						icon: '/static/imgs/live.png',
						txt: '扫码核销',
						isFree: false
					},
					{
						bg: 'linear-gradient(0deg,rgba(255,126,34,1),rgba(240,184,27,1))',
						icon: '/static/imgs/emblem.png',
						txt: '营销活动',
						isFree: true
					},
					{
						bg: 'linear-gradient(0deg,rgba(9,177,252,1),rgba(24,200,255,1))',
						icon: '/static/imgs/question_bank.png',
						txt: '分享店铺',
						isFree: true
					}
				],
				second_menus: [{
						icon: '/static/imgs/exam.png',
						path:'',
						txt: '我的客户'
					},
					{
						icon: '/static/imgs/textbook.png',
						path:'',
						txt: '我的业绩',
					},
					{
						icon: '/static/imgs/book_ticket.png',
						path:'',
						txt: '出库领料'
					},
					{
						icon: '/static/imgs/more.png',
						path:'/pages/index/allop',
						txt: '全部功能'
					}
				],
				records: [{
						bg: 'linear-gradient(-30deg,rgba(171,218,255,1),rgba(215,239,255,1))',
						title: '教师考情分析',
						mainTeacher: '小A',
						subTitle: '标题名称',
						subColor: '#15639F',
						icon: '/static/test2.png',
						isFree: true
					},
					{
						bg: 'linear-gradient(-30deg,rgba(192,253,227,1),rgba(224,252,240,1))',
						title: '查看详情',
						mainTeacher: '小B',
						subTitle: '标题名称',
						subColor: '#07B77B',
						icon: '/static/test.png',
						isFree: false
					},
					{
						bg: 'linear-gradient(-30deg,rgba(171,218,255,1),rgba(215,239,255,1))',
						title: '教师考情分析',
						mainTeacher: '小A',
						subTitle: '标题名称',
						subColor: '#15639F',
						icon: '/static/test2.png',
						isFree: true
					}
				]
			}
		},
		onLoad() {

		},
		methods: {
			toCustonData(id){
				uni.navigateTo({
					url: '/pages/index/customdata?id='+id
				})
			}
		}
	}
</script>

<style>
	page {
		width: 100%;
	}
	.swiper{
		height: 450rpx;
	}
	.grid-text {
		font-size: 14px;
		color: #909399;
		padding: 10rpx 0 20rpx 0rpx;
		/* #ifndef APP-PLUS */
		box-sizing: border-box;
		/* #endif */
	}
</style>
<style lang="scss" scoped>
	@function realSize($args) {
		@return $args / 1.5;
	}

	.page_car {
		width: 100%;
	}

	.page_car_header {
		padding-top: var(--status-bar-height);
		background-color: #208eff;
		width: 100%;
		height: realSize(350px);

		.header {
			display: flex;
			flex-direction: row;
			align-items: center;
			padding: realSize(20px);

			.btn {
				width: realSize(36px);
				height: realSize(30px);
			}

			.input {
				height: realSize(59px);
				width: 100%;
				margin-left: realSize(20px);
				margin-right: realSize(20px);
				background: rgba(255, 255, 255, 1);
				border-radius: realSize(30px);
				display: flex;
				flex-direction: row;
				align-items: center;

				.search {
					width: realSize(30px);
					height: realSize(30px);
					margin-left: realSize(20px);
					margin-right: realSize(20px);
				}
			}
		}

		.header_content {
			display: flex;
			flex-direction: row;

			.left {
				display: flex;
				flex-direction: column;
				width: 60%;
				margin-top: 10px;
				margin-left: 15px;
				margin-right: 15px;

				.title {
					width: realSize(419px);
					height: realSize(59px);
					font-size: realSize(47px);
					font-weight: bold;
					color: rgba(255, 255, 255, 1);
				}

				.sub_title {
					margin-top: 3px;
					font-size: realSize(18px);
					font-weight: 400;
					color: rgba(255, 255, 255, 1);

					background: linear-gradient(0deg, rgba(120, 255, 224, 1) 0%, rgba(255, 255, 255, 1) 100%);
					-webkit-background-clip: text;
					-webkit-text-fill-color: transparent;
				}

				.btn {
					margin-top: 3px;
					width: realSize(198px);
					height: realSize(60px);
					background: linear-gradient(-30deg, rgba(252, 135, 29, 1), rgba(246, 185, 9, 1));
					box-shadow: 0px 4px 10px 0px rgba(255, 121, 0, 0.5);
					border-radius: realSize(30px);
					color: rgba(255, 255, 255, 1);
					display: flex;
					align-items: center;
					justify-content: center;
				}
			}
		}
	}

	.page_content {
		width: 100%;
		margin-top: -150rpx;
		.menu {
			margin-left: 10px;
			margin-right: 10px;
			padding-left: 10px;
			padding-right: 10px;
			height: realSize(176px);
			background: rgba(255, 255, 255, 1);
			box-shadow: 0px 10px 10px 0px rgba(0, 161, 124, 0.1);
			border-radius: 10px;
			display: flex;
			flex-direction: row;
			align-items: stretch;
			justify-content: space-between;

			.item {
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: center;
				&:active{
					opacity: .5;
				}
				.img_view {
					width: 60px;
					height: 60px;
					border-radius: 30px;
					display: flex;
					align-items: center;
					justify-content: center;

					.image {
						width: 50px;
						height: 50px;
					}
				}

				.txt {
					margin-top: 5px;
					font-size: 14px;
					color: rgba(51, 51, 51, 1);
				}
			}
		}

		.s_menu {
			display: flex;
			flex-direction: row;
			align-items: stretch;
			justify-content: space-between;
			margin: 60rpx 20rpx;
			padding-left: 10px;
			padding-right: 10px;

			.item {
				.path-hover{
					opacity: .5;
				}
				.path {
				    display: flex;
				    flex-direction: column;
				    justify-content: center;
				    align-items: center;
					padding: 10rpx;
					.image {
						width: 35px;
						height: 35px;
					}
					.txt {
						margin-top: 5px;
						font-size: 14px;
						color: rgba(51, 51, 51, 1);
					}
				}
			}
		}

	}

</style>
