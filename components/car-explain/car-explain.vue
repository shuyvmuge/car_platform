<template>
	<swiper class="swiper" :style="`height: ${ rpxHeight }rpx`" changing-class="changing-class" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
		<swiper-item class="swiper-item">
			<image  :src="src" mode="widthFix"></image>
		</swiper-item>
	</swiper>
</template>

<script>
export default {
	name:'CarExplain',
	props:{
		src:{
			type:String,
			default:'https://wmslab.youyiweizhan.com/attachment/images/2/2021/04/OBNapBPbiiAebmXEIiEXPeV3FFh1e4.png'
		},
		autoplay:{
			type:Boolean,
			default:true
		},
		interval:{
			type:Number,
			default:2000
		},
		duration:{
			type:Number,
			default:1500
		},
		height:{
			type:Number,
			default:75
		},
	},
    data() {
        return {
			indicatorDots:false,
			rpxHeight:this.height*2
		}
    },
    methods: {
        
    }
}	
</script>

<style lang="scss" scoped>
	.swiper{
		.swiper-item{
			border-radius: 10rpx;
		}
		image{
			width: 100%;
			border-radius: 10rpx;
		}
	}
	.changing-class{
		border-radius: 10rpx;
	}
</style>
