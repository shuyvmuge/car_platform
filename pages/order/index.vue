<template>
	<view class="content">
		<view>
			<view class="">
				<view>最多选 {{ max }} 个</view>
				<view>已选 {{ count }} 个</view>
				<button @click="getCurrentItem">获取当前索引</button>
			</view>
			
			<long-categories
				ref="long"
				:list="list"
				:maxSelected="max"
				@change="change"
			>
			</long-categories>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				list: [
					{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},{
						id:1,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤EP9875'
							}
						]
					},
				],
				count: 0,
				max: 10
			}
		},
		onLoad() {
			this.init()
		},
		methods: {
			init () {
			},
			change (data) {
				this.count = data.length
				console.log(data)
			},
			getCurrentItem () {
				console.log(this.list)
			}
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
