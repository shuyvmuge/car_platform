<template>
	<view class="car-data">
		<view class="car-container" :style="`width:calc(${width} - 20rpx)` " v-for="(item,index) in datas" :key="index" @click="click(item)">
			<view class="car-name">{{item.name}}</view>
			<view class="car-num">{{item.data}}</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"CarData",
		props:{
			datas:{
				type:Array,
				default:new Array
			},
			width:{
				type:String,
				default:'25%'
			}
		},
		data() {
			return{
				
			}
		},
		methods:{
			click(e){
				this.$emit('click',e)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.car-data{
		width: 100%;
		display: flex;
		justify-content: flex-start;
		align-items: center;
		flex-wrap: wrap;
		.car-container{
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			padding: 20rpx 0;
			background-color: #f7f7f7;
			margin: 10rpx;
			&:active{
				opacity: .5;
			}
			.car-name{
				text-align: center;
			}
			.car-num{
				font-size: 1.5em;
				text-align: center;
			}
		}
	}
</style>
