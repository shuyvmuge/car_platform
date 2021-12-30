<template>
	<view class="car-action">
		<u-grid
			v-if="actions.length > 0"
			:border="false"
			align="left"
			col="4"
		>
			<u-grid-item
				v-for="(item,index) in actions"
				:key="index"
				style="margin:16rpx 0;"
				@click="click(item)"
			>
				<u-icon
					:name="item.name"
					:size="28"
					color="#208eff"
				></u-icon>
				<text class="grid-text">{{item.title}}</text>
			</u-grid-item>
		</u-grid>
	</view>
</template>

<script>
	export default{
		name:'CarAction',
		props:{
			actions:{
				type:Array,
				default:new Array
			}
		},
		methods:{
			click(e){
				this.$emit('click', e)
			}
		}
	}
</script>

<style>
</style>
