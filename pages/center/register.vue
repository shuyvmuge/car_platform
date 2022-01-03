<template>
	<view class="sun-index">
		<view class="sun-login-box">
			<view class="sun-label">
				<u-icon name="home" size="30" color="#272e2d"></u-icon>
				<text class="label-text">店铺名称</text>
			</view>
			<view class="sun-input-box">
				<input v-model="store" type="text" placeholder="请输入当前经营店铺名称" placeholder-class="placeholder-class"/>
				<u-icon v-show="store" @click="store=''" name="close-circle" size="28" color="#d4d7d6"></u-icon>
			</view>
		</view>
		
		<view class="sun-login-box">
			<view class="sun-label">
				<u-icon name="map" size="30" color="#272e2d"></u-icon>
				<text class="label-text">店铺地址</text>
			</view>
			<view class="sun-input-box">
				<input v-model="address" type="text" placeholder="请输入店铺详细地址" placeholder-class="placeholder-class"/>
				<u-icon v-show="address" @click="address=''" name="close-circle" size="28" color="#d4d7d6"></u-icon>
			</view>
		</view>
		
		<view class="sun-login-box">			<view class="sun-label">				<u-icon name="phone" size="30" color="#272e2d"></u-icon>				<text class="label-text">手机</text>			</view>			<view class="sun-input-box">				<input v-model="mobile" type="text" placeholder="请输入手机号" placeholder-class="placeholder-class"/>
				<u-icon v-show="mobile" @click="mobile=''" name="close-circle" size="28" color="#d4d7d6"></u-icon>			</view>		</view>
				<view class="sun-login-box">			<view class="sun-label">				<u-icon name="email" size="30" color="#272e2d"></u-icon>				<text class="label-text">验证码</text>			</view>			<view class="sun-input-box">				<input v-model="code" type="text" placeholder="请输入验证码" placeholder-class="placeholder-class"/>
				<u-icon v-show="code" @click="code=''" name="close-circle" size="28" color="#d4d7d6" style="margin-right: 100rpx;"></u-icon>				<text class="code-text" :class="{gray:showTime}" @click="handleGetCodeClick">{{showTime ?currentCountTime+'s后重新获取':'获取验证码'}}</text>			</view>		</view>
				<view class="sun-login-box">			<view class="sun-label">				<u-icon name="lock" size="30" color="#272e2d"></u-icon>				<text class="label-text">密码</text>			</view>			<view class="sun-input-box">				<input v-model="password" type="password" placeholder="请输入密码" placeholder-class="placeholder-class"/>
				<u-icon v-show="password" @click="password=''" name="close-circle" size="28" color="#d4d7d6"></u-icon>			</view>		</view>
		<view class="sun-login-box">
			<view class="sun-label">
				<u-icon name="lock" size="30" color="#272e2d"></u-icon>
				<text class="label-text">确认密码</text>
			</view>
			<view class="sun-input-box">
				<input v-model="passconfirm" type="password" placeholder="请输入密码" placeholder-class="placeholder-class"/>
				<u-icon v-show="passconfirm" @click="passconfirm=''" name="close-circle" size="28" color="#d4d7d6"></u-icon>
			</view>
		</view>
		
		<car-btn title="提交审核" @click="handleSubmit"></car-btn>	</view>
</template>

<script>
	export default {
		data() {
			return {
				store:'',
				address:'',
				mobile:'',				password:'',
				passconfirm:'',				code:'',				countTime: 60, 				currentCountTime: 0,				showTime:false,				timeId:null
			}
		},		created() {			this.currentCountTime = this.countTime		},
		onLoad() {

		},
		methods: {
			handleSubmit() {				if(!this.store) return uni.showToast({title: '请输入店铺名称',icon:'none',duration: 1500})				if(!this.address) return uni.showToast({title: '请输入详细地址',icon:'none',duration: 1500})				if(!this.mobile) return uni.showToast({title: '请输入手机号',icon:'none',duration: 1500})				if(!this.code) return uni.showToast({title: '请输入验证码',icon:'none',duration: 1500})				if(!this.password) return uni.showToast({title: '请输入密码',icon:'none',duration: 1500})
				if(this.password != this.passconfirm) return uni.showToast({title: '两次密码输入不一致',icon:'none',duration: 1500})				uni.showToast({title: '提交成功,我们会尽快审核',duration: 1500})			},			handleGetCodeClick() {				this.showTime = true				if(this.showTime && this.currentCountTime !== this.countTime) return				this.currentCountTime				this.timeId = setInterval(()=>{					if(this.currentCountTime <= 0) {						this.currentCountTime = this.countTime						this.showTime = false						clearInterval(this.timeId)					}					this.currentCountTime--				},1000)			}
		}
	}
</script>

<style scoped>	.sun-login-box {		padding: 20rpx 60rpx;	}	.sun-label {		display: flex;		align-items: center;	}	.label-text {		margin-left: 16rpx;		font-weight: 500;		color: #272e2d;		font-size: 30rpx;	}	.sun-input-box {		display: flex;		align-items: center;		height: 100rpx;		border-bottom: 1rpx solid #eee;		padding: 0px 10rpx;	}	.sun-input-box input {		flex: 1;	}	.placeholder-class {		font-size: 30rpx;		color: #C0C0C0;	}	.sun-tip {		display: flex;		justify-content: space-between;		padding: 0rpx 68rpx;	}	.sun-tip-text {		color: #30C6B3;	}		.code-text {		font-size: 28rpx;		color: #208eff;	}	.gray {		color: #C0C0C0;	}</style>
