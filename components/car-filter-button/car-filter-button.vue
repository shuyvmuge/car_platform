<template>
	<view :class="topFixed?'select-tab-fixed-top':'select-tab'" :style="{backgroundColor:color,padding:'20rpx 0'}">
		<view class="select-tab-item" v-for="(item,index) in filters" :key="index" @tap="click(item)">
			<text>{{item.title}}</text>
			<text class="arrows sl-font sl-down"></text>
		</view>
	</view>
</template>

<script>
	export default {
		name:'CarFilterButton',
		props: {
			filters: {
				type: Object,
				default: new Object
			},
			height:{
				type: String,
				default: '60'
			},
			color:{
				type: String,
				default: '#f7f7f7'
			},
			topFixed:{
				type:Boolean,
				default:true
			}
		},

		data() {
			return {
				down: 'sl-down',
				up: 'sl-up',
				tabHeight: 50,
				statusList: [],
				selectedIndex: '',
				titleList: [],
				tempTitleObj: {}
			};
		},
		methods: {
			click(e) {
				this.$emit('click',e)
			}
		}
	}
</script>

<style scoped>
	@import 'iconfont.css';

	.select-tab {
		width: 100%;
	}

	.select-tab-fixed-top {
		width: 100%;
		position: fixed;
		top: 44px;
		z-index: 999;
	}

	.arrows {
		margin-left: 5px;
	}

	.select-tab-item{
		height: auto;
		background-color: #ffffff;
		padding: 15rpx 20rpx;
		margin: 20rpx;
		margin-top: 10rpx;
		border-radius: 100rpx;
		float: left;
	}
	
	.select-tab-item:active{
		opacity: .5;
	}

	.select-tab-item text {
		color: #666666;
		font-size: 14px;
		
	}
</style>
