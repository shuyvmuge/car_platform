<template>
	<view class="profile">
		<view class="explain">
			<car-explain :height="80"></car-explain>
		</view>
		<view class="action">
			<car-action :actions="teamMenus" @click="menuAction"></car-action>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				teamMenus: [{
						name: 'plus-square-fill',
						title: '新增'
					},
					{
						name: 'account-fill',
						title: '客户分析'
					}]
			}
		}
	}
</script>

<style lang="scss" scoped>
	.profile{
		margin: auto 30rpx;
		.explain{
			margin: 30rpx auto;
		}
	}
</style>
