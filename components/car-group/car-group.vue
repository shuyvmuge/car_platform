<template>
	<view class="car-group" :class="['car-group--'+mode ,margin?'group-margin':'']" :style="{marginTop: `${top}px` }">
		<slot name="title">
			<view class="group_icon_con">
				<view class="group_icon"></view>
			</view>
			<view v-if="title" class="car-group__title" :style="{'padding-left':border?'30px':'15px'}">
				<text class="car-group__title-text">{{ title }}</text>
			</view>
		</slot>
		<view class="car-group__content" :class="{'group-conent-padding':border}">
			<slot />
		</view>
	</view>
</template>

<script>
	/**
	 * Group 分组
	 * @description 表单字段分组
	 * @tutorial https://ext.dcloud.net.cn/plugin?id=3281
	 * @property {String} title 主标题
	 * @property {Number} top 分组间隔
	 * @property {Number} mode 模式
	 */
	export default {
		name: 'car-group',
		emits:['click'],
		props: {
			title: {
				type: String,
				default: ''
			},
			top: {
				type: [Number, String],
				default: 10
			},
			mode: {
				type: String,
				default: 'default'
			}
		},
		data() {
			return {
				margin: false,
				border: false
			}
		},
		watch: {
			title(newVal) {
				if (uni.report && newVal !== '') {
					uni.report('title', newVal)
				}
			}
		},
		methods: {
			/**
			 * 获取父元素实例
			 */
			onClick() {
				this.$emit('click')
			}
		}
	}
</script>
<style lang="scss" scoped>
	.car-group {
		background: #fff;
		margin-top: 10px;
		// border: 1px red solid;
	}
	.group-margin {
		// margin: 0 -15px;
	}

	.group_icon_con{
		display: flex;
		justify-content: center;
		align-items: center;
		float: left;
		height: 40px;
		width: 5px;
		background-color: #eee;
		.group_icon{
			background-color: #208eff;
			width: 100%;
			height: 22px;
		}
	}
	
	.car-group__title {
		/* #ifndef APP-NVUE */
		display: flex;
		/* #endif */
		flex-direction: row;
		align-items: center;
		padding-left: 15px;
		height: 40px;
		background-color: #eee;
		font-weight: normal;
		color: #666;
	}

	.car-group__content {
		padding: 15px;
		// padding-bottom: 5px;
		// background-color: #FFF;
	}

	.group-conent-padding {
		padding: 0 15px;
	}

	.car-group__title-text {
		font-size: 14px;
		color: #333333;
	}

	.distraction {
		flex-direction: row;
		align-items: center;
	}

	.car-group--card {
		margin: 10px;
		border-radius: 5px;
		overflow: hidden;
		box-shadow: 0 0 5px 1px rgba($color: #000000, $alpha: 0.08);
	}
</style>
