<template>
	<view class="itemList">
		<view class="explain">
			<car-explain :height="80"></car-explain>
		</view>

		<view class="car-card">
			<car-card
				:title="itemList.title" 
				:subTitle="itemList.sub_title" 
				extraIcon="/static/imgs/circle_right.png"
				:is-full="true" 
				:border="true"
				shadow="true"
				padding="0"
				spacing="0"
				@click="customer"
			>
				<view class="car-data">
					<car-data :datas="itemList.datas" width="50%" @click="dataAction"></car-data>
				</view>
				<uni-list :border="false">
					<car-list-item
						:border="false"
						:title="fastItems.title"
						:note="fastItems.sub_title" 
						:rightText="fastItems.items"
						:thumb="fastItems.icon"
						:showArrow="true"
					>
					</car-list-item>
					 <car-list-item 
						:border="true"
						v-for="(item,index) in itemList.items"
						:key="index"
						:title="item.title" 
						:showArrow="true"
						:showBadge="true"
						badgeType="primary"
						:badgeText="item.badgeText"
						:thumb="item.icon"
					>
					</car-list-item>
				</uni-list>
			</car-card>
			<view style="margin: 30rpx;"></view>
			<car-card
				:title="itemsSelf.title" 
				:subTitle="itemsSelf.sub_title" 
				extraIcon="/static/imgs/circle_right.png"
				:is-full="true" 
				:border="true" 
				shadow="true"
				padding="0"
				spacing="0"
				@click="customer"
			>
				<uni-list :border="false">
					 <car-list-item 
						:border="true"
						v-for="(item,index) in itemsSelf.items"
						:key="index"
						:title="item.title" 
						:showArrow="true"
						:showBadge="true"
						badgeType="primary"
						:badgeText="item.badgeText"
						:thumb="item.icon"
					>
					</car-list-item>
				</uni-list>
			</car-card>
		</view>
		<car-btn title="新增项目" position="fixed" icon="plus-circle"></car-btn>
	</view>
</template>

<script>
	export default{
		data(){
			return{				
				itemList:{
					title:'标准项目',
					sub_title:'项目总数：30608',
					datas:[{
							id:1,
							name:'正常',
							data:1380,
						},
						{
							id:1,
							name:'已禁用',
							data:'500',
						}],
					items:[
						{
							title:'美容项目',
							icon:'/static/imgs/order.png',
							badgeText:'200'
						},
						{
							title:'机修',
							icon:'/static/imgs/order.png',
							badgeText:'1700'
						},
						{
							title:'工时',
							icon:'/static/imgs/order.png',
							badgeText:'2000'
						},
						{
							title:'保养',
							icon:'/static/imgs/order.png',
							badgeText:'100'
						},
						{
							title:'车管业务',
							icon:'/static/imgs/order.png',
							badgeText:'1500'
						}
					]
				},
				fastItems:{
					title:'快捷项目',
					sub_title:'接车时一键快捷开单',
					items:'洗车 | 换胎',
					icon:'/static/imgs/order.png',
				},
				itemsSelf:{
					title:'员工自定义项目',
					sub_title:'项目总数：608',
					items:[
						{
							title:'美容项目',
							icon:'/static/imgs/order.png',
							badgeText:'200'
						},
						{
							title:'机修',
							icon:'/static/imgs/order.png',
							badgeText:'1700'
						},
						{
							title:'工时',
							icon:'/static/imgs/order.png',
							badgeText:'2000'
						},
						{
							title:'保养',
							icon:'/static/imgs/order.png',
							badgeText:'100'
						},
						{
							title:'车管业务',
							icon:'/static/imgs/order.png',
							badgeText:'1500'
						}
					]
				},
			}
		},
		methods:{
			menuAction(e){
				console.log(e)
				uni.navigateTo({
					url:e.url
				})
			},
			dataAction(e){
				console.log(e)
			},
			customer(e){
				console.log(e)
				switch(e){
					case 'title':
						uni.navigateTo({
							url:'/pages/menus/profile/list'
						})
					case 'extra':
						uni.navigateTo({
							url:'/pages/menus/profile/list'
						})
				}
			}
		}
	}
</script>

<style lang="scss" scoped>
	.itemList{
		.explain{
			margin: 30rpx;
		}
		.car-card{
			margin: 30rpx;
		}
		.car-data{
			margin: 20rpx auto;
		}
	}
</style>
