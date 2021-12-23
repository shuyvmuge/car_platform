<template>
	<view>
		<u-form v-for="(item,is) in auth">
			<u-form-item class="u-form-item" labelWidth="80" :key="is" :label="item.title">
				<u-switch 
					slot="right" 
					v-model="item.value" 
					activeColor="#208eff" 
					inactiveColor="rgb(230, 230, 230)" 
					@change="cardchange"
				>
				</u-switch>
			</u-form-item>
		</u-form>
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
		console.log(options)
		var pages = getCurrentPages();
		var prevPage = pages[pages.length - 2]; //上一个页面
		this.auth = prevPage.$vm.userInfo.authes[this.index].auth[this.i].children
		console.log(this.auth)
	},
	methods:{
		itemClick(brand){
			
			var pages = getCurrentPages();
			var prevPage = pages[pages.length - 2]; //上一个页面
			prevPage.$vm.form.brand = brand
			uni.navigateBack({//返回
				delta: 1
			})
		}
	}
}
</script>

<style>
</style>
