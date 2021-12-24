<template>
	<view>
		<car-card>
			<u-form v-for="(item,index) in auth">
				<u-form-item class="u-form-item" labelWidth="80" :key="index" :label="item.title">
					<u-switch 
						slot="right" 
						v-model="item.value" 
						activeColor="#208eff" 
						inactiveColor="rgb(230, 230, 230)" 
					>
					</u-switch>
				</u-form-item>
			</u-form>
		</car-card>
		<car-btn title="确定" style="margin-top: 0;" @click="submit"></car-btn> 
	</view>
</template>

<script>
export default{
	data(){
		return{
			auth:[]
		}
	},
	onLoad(options) {
		this.index = options.index
		this.i = options.i
		var pages = getCurrentPages();
		var prevPage = pages[pages.length - 2]; //上一个页面
		this.auth = prevPage.$vm.userInfo.authes[this.index].auth[this.i].children
		console.log(this.auth)
	},
	methods:{
		submit(){
			var pages = getCurrentPages();
			var prevPage = pages[pages.length - 2]; //上一个页面
			prevPage.$vm.userInfo.authes[this.index].auth[this.i].children = this.auth
			uni.navigateBack({//返回
				delta: 1
			})
		}
	}
}
</script>

<style>
</style>
