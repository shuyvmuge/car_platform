<template>
	<view>
		<view 
			class="car-button-container"
			:style="{background:bg}"
			@click="click(item)"
		>
			<u-icon v-if="icon" :name="icon" :color="color"></u-icon>
			<text class="car-button" :style="{color:color}">{{text}}</text>
		</view>
	</view>
</template>

<script>
	export default{
		name:'CarButton',
		props:{
			text:{
				type:String,
				default:'按钮'
			},
			color:{
				type:String,
				default:''
			},
			icon:{
				type:String,
				default:''
			},
			bg:{
				type:String,
				default:''
			}
		},
		methods:{
			click(e) {
				this.$emit('click', e)
			}
		}
	}
</script>

<style lang="scss" scoped>
	.car-button-container{
		width: auto;
		display: flex;
		justify-content: center;
		text-align: center;
		padding: 5px 8px;
		margin: 8px;
		border-radius: 50px;
		border: 1px solid rgba($color: #208eff, $alpha: .2);
		&:active{
			// opacity: .5;
			background: rgba($color: #208eff, $alpha: .2);
			color: #ffffff;
		}
	}
</style>
