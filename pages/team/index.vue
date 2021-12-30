<template>
    <view class="team-contanner">
		<view class="team-header">
			<car-explain src="https://cdn.uviewui.com/uview/swiper/swiper2.png"></car-explain>
		</view>
		
		<view class="team-menu">
			<car-action :actions="teamMenus" @click="menuAction"></car-action>
		</view>
		
		<view class="team-list" v-for="(item,indexs) in uList" :key="indexs">
			<car-card :title="item.title" :is-full="true" :border="false" padding="0">
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
					@click="staffEdit(child)"
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
				form:{},
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
			
				teamMenus: [{
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
				},
				{
					name: 'file-text-fill',
					title: '操作记录'
				},
				{
					name: 'file-text-fill',
					title: '操作记录'
				},
				{
					name: 'file-text-fill',
					title: '操作记录'
				},
				{
					name: 'file-text-fill',
					title: '操作记录'
				}]
			}
		},
		methods:{
			staffEdit(e){
				if(e.id == undefined) uni.showToast({title:'参数错误',icon:'none',duration: 1500});
				uni.navigateTo({
					url:'/pages/team/edit?id='+e.id
				})
			},
			menuAction(e){
				console.log(e)
			}
		},
		onShow(){
		   var that = this;
		   var pages = getCurrentPages();
		   console.log('1111111')//为传过来的值
		   console.log(pages)//为传过来的值vm.form
		   console.log('22222222')//为传过来的值
		   console.log('33333333')//为传过来的值
		   console.log(pages[pages.length - 1].$vm.form.name)//为传过来的值vm.form
		   console.log('444444444')//为传过来的值
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
	.team-contanner{
		width: 100%;
		.team-header{
			padding: 30rpx;
		}
		.team-menu{
			padding: 10rpx 0 40rpx 0;
			
		}
		.slot-image{
			width: 90rpx;
			height: 100rpx;
		}
	}
</style>
