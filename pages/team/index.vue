<template>
    <view class="team-contanner">
		<view class="team-header">
			<u-swiper
			        :list="list4"
			        keyName="url"
			        :autoplay="true"
					height="120rpx"
					radius="16rpx"
			></u-swiper>
		</view>
		
		<view class="team-menu">
			<u-grid
				:border="false"
				@click="click"
				align="left"
				col="4"
			>
				<u-grid-item
					v-for="(baseListItem,baseListIndex) in baseList"
					:key="baseListIndex"
				>
					<u-icon
						:customStyle="{paddingTop:20+'rpx'}"
						:name="baseListItem.name"
						:size="28"
						color="#208eff"
					></u-icon>
					<text class="grid-text">{{baseListItem.title}}</text>
				</u-grid-item>
			</u-grid>
		</view>
		
		<view class="team-list" v-for="(item,indexs) in uList" :key="indexs">
			<car-card :title="item.title" :is-full="true" :border="false">
				<uni-list
					v-for="(child, index1) in item.itemlist"
					:key="index1" 
					:border="false"
				>
					<uni-list-item 
					:border="false"
					:title="child['name']" 
					:note="child['tel']" 
					:thumb="child['avatar']"
					thumbSize="lg"
					@click="itemClick(child)"
					:rightText="child['auth_num']+'项权限'"
					link>
					</uni-list-item>
				</uni-list>
			</car-card>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				uList:[{
					title:'店长',
					itemlist:[
						{
							id:1,
							name:'张三',
							avatar:'http://t14.baidu.com/it/u=16381851,2678769536&fm=224&app=112&f=JPEG?w=500&h=500',
							tel:'18898875041',
							auth_num:9
						},
						{
							id:2,
							name:'张三',
							avatar:'http://t14.baidu.com/it/u=16381851,2678769536&fm=224&app=112&f=JPEG?w=500&h=500',
							tel:'18898875041',
							auth_num:8
						}
					]
				},{
					title:'前台',
					itemlist:[
						{
							id:3,
							name:'张三',
							avatar:'http://t14.baidu.com/it/u=16381851,2678769536&fm=224&app=112&f=JPEG?w=500&h=500',
							tel:'18898875041',
							auth_num:10
						},
						{
							id:4,
							name:'张三',
							avatar:'http://t14.baidu.com/it/u=16381851,2678769536&fm=224&app=112&f=JPEG?w=500&h=500',
							tel:'18898875041',
							auth_num:6
						}
					]
				}],
			    list4: [{
			        url: 'https://cdn.uviewui.com/uview/swiper/swiper2.png',
			        title: '身无彩凤双飞翼，心有灵犀一点通'
			    },{
			        url: 'https://cdn.uviewui.com/uview/swiper/swiper2.png',
			        title: '身无彩凤双飞翼，心有灵犀一点通'
			    }],
			
				baseList: [{
					name: 'plus-square-fill',
					title: '新增人员'
				},
				{
					name: 'account-fill',
					title: '职位设置'
				},
				{
					name: 'file-text-fill',
					title: '操作记录'
				}]
			}
		},
		methods:{
			itemClick(e){
				if(e.id == undefined) uni.showToast({title:'参数错误',icon:'none',duration: 1500});
				uni.navigateTo({
					url:'/pages/team/edit?id='+e.id
				})
			}
		},
		onLoad(options){
			console.log(options)
			uni.setNavigationBarTitle({
				title:options.title
			})
		}
	}
</script>

<style lang="scss" scoped>
	image{
		border-radius: 16rpx;
	}
	.team-contanner{
		width: 100%;
		.team-header{
			padding: 10rpx 30rpx;
		}
		.team-menu{
			padding-bottom: 30rpx;
			
		}
		.slot-image{
			width: 90rpx;
			height: 100rpx;
		}
	}
</style>
