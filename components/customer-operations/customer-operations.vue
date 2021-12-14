<template>
	<view class="car_grid">
		<view class="car_item" v-for="(item, index) in list" :key="item.id" :index="index" v-show="index > 2?kg:true">
			<view class="item_title">{{item.name}}</view>
			<view class="item_num">{{item.num}}</view>
			<view class="item_newadd">今日+{{item.today}}</view>
		</view>
		<view class="car_item_btn" @click="kg = !kg" v-show="list.length > 3">
			<view>
				<u-icon  v-if="kg == false" label="展开" labelPos="bottom" size="28" labelSize="14" name="/static/imgs/zk.png"></u-icon>
				<u-icon  v-else label="收起" labelPos="bottom" size="28" labelSize="14" name="/static/imgs/sq.png"></u-icon>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"customer-operations",
		props:{
			list:{
				type : Array,
				default: new Array
			}
		},
		data(){
			return {
				kg:false
			}
		},
		methods:{
			
		},
		created:function(e){
			console.log('car_grid 挂载了')
			console.log(this.list)
		},
	}
</script>

<style lang="scss" scoped>
	.car_grid{
		width: 100%;
		display: flex;
		justify-content: flex-start;
		align-items: center;
		flex-wrap: wrap;
		.car_item_btn{
			width: 25%;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
		}
		.car_item{
			width: 25%;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			padding: 10rpx;
			margin: 10rpx 0;
			// border-bottom: 1px solid #eee;
			.item_title{
				font-size: 14px;
				color: #333333;
			}
			.item_num{
				font-size: 20px;
				color: #208eff;
				padding: 10rpx 0;
			}
			.item_newadd{
				font-size: 14px;
				color: #C0C0C0;
			}
		}
	}
</style>
