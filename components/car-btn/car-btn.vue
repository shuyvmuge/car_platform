<template>
	<view :class="`car-container flex-center ${position}`"  @tap="clickHandler">
	   <view class="btn flex-center">
		   <u-icon
		   	:label="title" 
		   	size="24" 
		   	labelSize="18" 
			color="#ffffff"
			labelColor="#ffffff"
		   	:name="icon"
		   ></u-icon>
			
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
			},
			position:{
				type:String,
				default:''
			},
			icon:{
				type:String,
				default:''
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
	  background: rgba($color: #ffffff, $alpha: 1);
	  .btn{
	    background-color: #208eff;
	    border-radius: 60rpx;
	    width: 80%;
	    height: 81%;
		&:active{
			opacity: .8;
		}
	  }
	}
	.fixed{
		position: fixed;
		width: 100%;
		bottom: 0;
	}
	.flex-center{
	  display: flex;
	  justify-content: center;
	  align-items: center;
	}
</style>
