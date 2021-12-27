<template>
	<view class="car-container flex-center" @tap="clickHandler">
	   <view class="btn flex-center">
	     {{title}}
	   </view>
	</view>
</template>

<script>
	export default{
		name:'car-btn',
		props:{
			title:{
				type:String,
				default:'提交'
			}
		},
		methods: {
			// 此方法由u-grid-item触发，用于在u-grid发出事件
			clickHandler(name) {
				console.log('event clicked')
				this.$emit('click', name)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.car-container{
	  height: 100rpx;
	  margin-top: 100rpx;
	  .btn{
	    background-color: #208eff;
	    border-radius: 60rpx;
	    width: 80%;
	    color: white;
	    font-size: 1.1em;
	    height: 81%;
		&:active{
			opacity: .8;
		}
	  }
	}
	.flex-center{
	  display: flex;
	  justify-content: center;
	  align-items: center;
	}
</style>
