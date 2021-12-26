<template>
	<view class="car_grid">
		<view 
			class="car_item" 
			v-for="(item, index) in list" 
			:key="index" 
			:index="index" 
			v-show="index > 2?kg:true"
		>
			<view class="item_title">{{item.title}}</view>
			<view class="item_num" v-if="item.num">{{item.num}}</view>
			<view 
				class="item_button" 
				v-if="item.button"
				@click="setClick(item)"
			>{{item.button.text}}</view>
			
			<view 
				class="item_link" 
				v-if="item.link"
				@click="linkClick(item)"
			>
				<view class="item_link_text">{{item.link.text}}</view>
				<view class="item_link_note">{{item.link.note}}</view>
			</view>
			
			<view class="item_extra" v-if="item.extra">{{item.extra.text}}
				<text class="item_extra_num">{{item.extra.num}}</text>
			</view>
		</view>
		
		<view class="car_item_btn" @click="kg = !kg" v-show="list.length > 3">
			<view>
				<u-icon  
					v-if="kg == false" 
					label="展开" 
					labelPos="bottom" 
					size="28" 
					labelSize="14" 
					name="/static/imgs/zk.png"
				></u-icon>
				<u-icon  
					v-else label="收起" 
					labelPos="bottom" 
					size="28" 
					labelSize="14" 
					name="/static/imgs/sq.png"
				></u-icon>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		name:"CarGridBoard",
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
			setClick(e) {
				this.$emit('setClick', e)
			},
			linkClick(e) {
				this.$emit('linkClick', e)
			},
		}
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
			padding: 16rpx 0;
			margin: 10rpx 0 20rpx 0;
		}
		.car_item{
			width: 25%;
			display: flex;
			flex-direction: column;
			justify-content: center;
			align-items: center;
			padding: 16rpx 0;
			margin: 10rpx 0 0 0;
			border-bottom: 1px solid #eee;
			.item_title{
				font-size: 14px;
				color: #333333;
			}
			.item_num{
				font-size: 20px;
				color: #208eff;
				padding: 10rpx 0;
			}
			.item_button{
				padding: 10rpx 16rpx;
				border-radius: 32rpx;
				background: rgba($color: #208eff, $alpha: .2);
				font-size: .8em;
				color: #208eff;
				text-align: center;
				margin: 10rpx;
				&:active{
					background: rgba($color: #208eff, $alpha: .1);
				}
			}
			.item_link{
				display: flex;
				flex-direction: column;
				justify-content: center;
				align-items: center;
				line-height: 1;
				.item_link_text{
					font-size: .8em;
					margin: 10rpx;
					color: #208eff;
				}
				.item_link_note{
					font-size: 14px;
					color: #C0C0C0;
				}
			}
			.item_extra{
				font-size: 14px;
				line-height: 1;
				color: #C0C0C0;
				.item_extra_num{
					font-size: 16px;
				}
			}
		}
	}
</style>
