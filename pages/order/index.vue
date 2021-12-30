<template>
	<view>
		<view class="search">
			<u-search
				:show-action="false"
				shape="square"
			></u-search>
		</view>
		<view class="content">
			<car-left-tab
				ref="long"
				:list="list"
				:maxSelected="max"
				@change="change"
			>
			</car-left-tab>
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
								name:'粤111111',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:2,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875888',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							}
							
						],
						selectedIds:{}
					},{
						id:2,
						name:'待查车',
						children:[
							{
								id:1,
								name:'粤222222',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/026.jpg',
								checked: false,
								disabled: false
							},{
								id:2,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/026.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/026.jpg',
								checked: false,
								disabled: false
							}
						],
						selectedIds:{}
					},{
						id:3,
						name:'待报价',
						children:[
							{
								id:1,
								name:'粤333333',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:2,
								name:'粤EP9875',
								date:'2021-12-18 01:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							},{
								id:3,
								name:'粤EP9875',
								date:'2021-12-18 00:07:56',
								img:'http://cx1.ycqpmall.com/static/xyzs/brand/002.jpg',
								checked: false,
								disabled: false
							}
						],
						selectedIds:{}
					}
				],
				count: 0,
				max: 10
			}
		},
		methods: {
			change (data) {
				this.count = data.length
				// console.log(data)
			},
			getCurrentItem () {
				console.log(this.$refs.long.getActive())
			}
		},
		onLoad() {
			
		}
	}
</script>

<style>
	.search{
		width: 100%;
		position: fixed;
		z-index: 999;
	}
	.content {
		padding-top: 64rpx;
		width: 100%;
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