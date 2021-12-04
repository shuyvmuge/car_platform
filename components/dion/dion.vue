<template>
	<view>
		<view class="group">{{title}}</view>
	</view>
</template>

<script>
	export default {
		name:"dion",
		props:{
			title:{
				type:String,
				default:'标题'
			}
		},
		data(){
			return {
			}
		},
		created:function(e){
			console.log('division 挂载了')
		},
	}
</script>

<style scoped>
	.group{
		width: 100px;
		height: 100px;
	}
</style>
