<template>
	<view>
		<u-keyboard ref="uKeyboard" mode="car" :show="show" @change="valChange"  @backspace="backspace" @cancel="cancel" @confirm="confirm" :overlay="false"></u-keyboard>
		<u--input
			:value="value"
			placeholder="后置图标"
			suffixIcon="scan"
			suffixIconStyle="color: #909399"
			@focus="car_focus"
			@blur="car_blur"
		></u--input>
		<navigator url="/pages/login/login">登录</navigator>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				value: '',
				show: false
			}
		},
		methods:{
			valChange(val) {
				// 将每次按键的值拼接到value变量中，注意+=写法
				this.value += val;
				console.log(this.value);
			},
			backspace() {
				// 删除value的最后一个字符
				if(this.value.length) this.value = this.value.substr(0, this.value.length - 1);
				console.log(this.value);
			},
			confirm(){
				this.show = false
			},
			cancel(){
				this.show = false
			},
			car_focus(){
				this.show = true
			},
			car_blur(event){
				alert(event.detail.value)
			}
		},
		onLoad() {
			uni.setNavigationBarTitle({
			    title: '数帮小店'
			});
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
