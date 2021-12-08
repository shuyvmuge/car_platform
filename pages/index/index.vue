<template>
	<view class="page_car">
		<u-notice-bar :text="text1" mode="closable" bgColor="#208eff" color="#ffffff"></u-notice-bar>
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
				<template v-for="(it,i) in menus">
					<view class="item" :key="'menu_'+i">
						<view class="img_view" :style="{background: it.bg}">
							<image :src="it.icon" class="image"></image>
						</view>
						<text class="txt">{{it.txt}}</text>
					</view>
				</template>
			</view>
			<view class="s_menu">
				<template v-for="(it,i) in second_menus">
					<view class="item" :key="'s_menu_'+i">
						<navigator :url="it.path" class="path">
							<image :src="it.icon" class="image"></image>
							<text class="txt">{{it.txt}}</text>
						</navigator>
					</view>
				</template>
			</view>
			<!-- <view class="ad">
				<view class="ad_btn">
					<text class="title">教资面试课上线</text>
					<text class="sub_title">老用户现实立减100元</text>
				</view>
				<image src="/static/tag.png" class="bg"></image>
			</view> -->
		</view>
		<!-- <scroll-view scroll-x="true" class="slider">
			<template v-for="(it, i) in records">
				<view class="item" :key="'slider_item_'+i" :style="{background: it.bg, marginRight: i === records.length - 1 ? '15px' : '0px'}">
					<view class="item_content">
						<view class="title">
							<text class="first">{{it.title}}</text>
							<text class="main">主讲：{{it.mainTeacher}}</text>
							<text class="sub" :style="{color:it.subColor}">标题名称</text>
						</view>
						<image class="image" :src="it.icon"></image>
						<text class="free">免\n费</text>
					</view>
				</view>
			</template>
		</scroll-view> -->
		
		<uni-group title="客户运营" mode="card">
			<customer-operations :list="cO_list"></customer-operations>
		</uni-group>
	
		<uni-group title="经营看板" mode="card">
			<business-kanban :list="bK_list"></business-kanban>
		</uni-group>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				text1: 'uView UI众多组件覆盖开发过程的各个需求，组件功能丰富，多端兼容。让您快速集成，开箱即用',
				cO_list: [
					{
						id:1,
						name:'保养到期',
						num:9,
						today:2
					},
					{
						id:2,
						name:'保险到期',
						num:2,
						today:0
					},
					{
						id:3,
						name:'回访',
						num:19,
						today:2
					},
					{
						id:4,
						name:'预约',
						num:19,
						today:2
					},
					{
						id:5,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:6,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:7,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:8,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:9,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:10,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:11,
						name:'流失预警',
						num:19,
						today:2
					}
				],
				bK_list: [
					{
						id:1,
						name:'保养到期',
						num:9
					},
					{
						id:2,
						name:'保险到期',
						num:2
					},
					{
						id:3,
						name:'回访',
						num:19
					},
					{
						id:4,
						name:'预约',
						num:19
					},
					{
						id:5,
						name:'流失预警',
						num:19
					},
					{
						id:6,
						name:'流失预警',
						num:19
					},
					{
						id:7,
						name:'流失预警',
						num:19
					},
					{
						id:8,
						name:'流失预警',
						num:19
					},
					{
						id:9,
						name:'流失预警',
						num:19,
						today:2
					},
					{
						id:10,
						name:'流失预警',
						num:19
					},
					{
						id:11,
						name:'流失预警',
						num:19
					}
				],
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
			margin-top: 60rpx;
			margin-left: 10px;
			margin-right: 10px;
			padding-left: 10px;
			padding-right: 10px;

			.item {
				.path {
				    display: flex;
				    flex-direction: column;
				    justify-content: center;
				    align-items: center;
					
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

		.ad {
			width: 100%;
			display: flex;
			flex-direction: row;
			align-items: center;
			justify-content: center;

			.bg {
				position: absolute;
				width: 120px;
				height: 105px;
				left: 0;
			}

			.ad_btn {
				width: 100%;
				height: 63px;
				margin: 30px;
				background: linear-gradient(0deg, rgba(253, 155, 28, 1), rgba(251, 197, 33, 1));
				border-radius: 67px;
				display: flex;
				flex-direction: column;
				align-items: center;
				justify-content: center;

				.title {
					font-size: realSize(38px);
					font-family: PingFang-SC-Heavy;
					font-weight: 800;
					color: rgba(255, 255, 255, 1);
				}

				.sub_title {
					background: linear-gradient(0deg, rgba(255, 128, 37, 1), rgba(255, 153, 32, 1));
					box-shadow: 0px 4px 5px 0px rgba(92, 53, 48, 0.3), 0px 1px 0px 0px rgba(228, 228, 228, 1);
					border-radius: realSize(24px);
					font-size: realSize(24px);
					font-family: PingFang-SC-Heavy;
					font-weight: 800;
					font-style: italic;
					color: rgba(255, 236, 177, 1);
					line-height: realSize(26px);
				}
			}
		}
	}

	.slider {
		white-space: nowrap;
		width: 100%;
		background-color: white;

		.item {
			display: inline-block;
			margin-left: 15px;
			margin-top: 13px;
			margin-bottom: 13px;
			width: 60%;
			height: 125px;
			border-radius: 10px;

			.item_content {
				display: flex;
				flex-direction: row;

				.title {
					width: 36%;
					margin: 20px;
					display: flex;
					flex-direction: column;
					
					.first {
						font-size: 16px;
						color:rgba(46,65,69,1);
					}
					.main {
						font-size: 13px;
						color:rgba(79,103,101,1);
						margin-top: 5px;
					}
					.sub {
						width: 60px;
						font-size: 10px;
						margin-top: 20px;
						background:rgba(255,255,255,0.4);
						border-radius:5px;
						display: flex;
						align-items: center;
						justify-content: center;
					}
				}

				.image {
					margin-top: 35px;
					width: 80px;
					height: 80px;
				}

				.free {
					background: rgba(11, 147, 252, 1);
					border-radius: 0px 0px 22px 22px;
					width: 25px;
					height: 50px;
					display: flex;
					align-items: center;
					justify-content: center;
					color: #FFFFFF;
					font-size: 14px;
				}
			}
		}
	}
</style>
