<template>
	<view class="profile">
		<view class="explain">
			<car-explain :height="80"></car-explain>
		</view>
		<view class="action">
			<car-action :actions="teamMenus" @click="menuAction"></car-action>
		</view>

		<view class="car-card">
			<car-card
				:title="profile.title" 
				:subTitle="profile.sub_title" 
				extraIcon="/static/imgs/circle_right.png"
				:is-full="true" 
				:border="false" 
				padding="0"
				spacing="0"
				@click="customer"
			>
				<car-data :datas="profile.datas" width="33%" @click="dataAction"></car-data>
				<uni-list :border="false">
					 <car-list-item 
						:border="false"
						v-for="(item,index) in profile.list"
						:key="index"
						:title="item.title" 
						:showArrow="true"
						:showBadge="true"
						badgeType="primary"
						:badgeText="item.badgeText"
						:rightText="item.rightText"
					>
					</car-list-item>
				</uni-list>
			</car-card>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return{
				
				teamMenus: [{
					name: 'plus-square-fill',
					title: '新增',
					url:'/pages/menus/profile/add'
				},
				{
					name: 'account-fill',
					title: '客户分析'
				}],
				
				profile:{
					title:'客户档案',
					sub_title:'档案总数：30608',
					datas:[{
							id:1,
							name:'车辆',
							data:1380,
						},
						{
							id:1,
							name:'覆盖率',
							data:'50%',
						},
						{
							id:1,
							name:'本月新增',
							data:130,
					}],
					list:[
						{
							title:'手机号',
							rightText:'覆盖率35%',
							badgeText:'1500'
						},
						{
							title:'车架号',
							rightText:'覆盖率5%',
							badgeText:'900'
						},
						{
							title:'驾驶证',
							rightText:'覆盖率3%',
							badgeText:'10'
						},
						{
							title:'行驶证',
							rightText:'覆盖率9%',
							badgeText:'50'
						}
					]
				}
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
	.profile{
		.explain{
			margin: 30rpx;
		}
		.action{
			margin-bottom: 30rpx;
		}
		.car-card{
			margin: 30rpx;
		}
	}
</style>
