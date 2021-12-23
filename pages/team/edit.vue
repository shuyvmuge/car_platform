<template>
	<view class="car_form">
		<u-form :model="userInfo" ref="uForm" labelPosition="left">
			<uni-card>
				<u-form-item
						v-for="(b,bi) in userInfo.base" :key="bi"
						class="u-form-item"
						:label="b.title"
						labelWidth="80" 
						:prop="b.name"
						borderBottom="true"
				>
					<u-input
						v-model="b.value"
						:placeholder="b.placeholder"
						:border="b.border"
						:type="b.type"
					></u-input>
				</u-form-item>
			</uni-card>
			<uni-card v-for="(item,index) in userInfo.authes" :title="item.title"  :key="index">
				<view v-if="item.level == 1" v-for="(a,i) in item.auth">
					<u-form-item class="u-form-item" labelWidth="80" :key="i" :label="a.title">
						<u-switch 
							slot="right" 
							v-model="a.value" 
							activeColor="#208eff" 
							inactiveColor="rgb(230, 230, 230)" 
							@change="cardchange"
						>
						</u-switch>
					</u-form-item>
				</view>
				<view v-else>
					<uni-list :key="i" :border="false">
						<uni-list-item 
							:title="a.title"
							 @click="itemClick(index,i)" 
							 rightText="全部可用" 
							 link
						 >
						</uni-list-item>
					</uni-list>
				</view>
			</uni-card>
		<car-btn title="确定" style="margin-top: 0;" @click="submit"></car-btn> 
		</u-form>
	</view>
</template>
 
<script>
export default {
	data() {
		return {
			form: {
				username:''
			},
			userInfo:{
				base:[
					{
						title:'姓名',
						type:'text',
						name:'username',
						border:'none',
						value:'张三',
						placeholder:'请输入姓名',
						
					},
					{
						title:'手机',
						type:'number',
						name:'tel',
						border:'none',
						value:'18898875041',
						placeholder:'请输入姓名',
						
					}
				],
				authes:[
					{	
						id:1,
						title:'特殊权限',
						level:1,
						auth:[
							{	
								id:109,
								path:'1-1',
								title:'活动授权',
								value:0,
							},
							{
								id:107,
								path:'1-2',
								title:'拨打电话',
								value:1,
							},
							{
								id:106,
								path:'1-3',
								title:'权限管理',
								value:0,
							},
							{
								id:105,
								path:'1-4',
								title:'员工管理',
								value:0,
							}
						]
					},
					{	id:2,
						title:'业务功能',
						level:2,
						auth:[
							{	id:10,
								title:'工单',
								children:[
									{
										id:101,
										path:'2-10-1',
										title:'开单',
										value:0,
									},
									{
										id:102,
										path:'2-10-2',
										title:'提车',
										value:1,
									},
									{
										id:103,
										path:'2-10-3',
										title:'买单',
										value:0,
									}
								]
							},
							{
								id:11,
								title:'订单',
								children:[
									{
										id:123,
										path:'2-11-1',
										title:'查看',
										value:0,
									},
									{
										id:112,
										path:'2-11-2',
										title:'办理',
										value:1,
									},
									{
										id:132,
										path:'2-11-3',
										title:'退改删',
										value:0,
									}
								]
							}
						]
					},
					{
						id:3,
						title:'营销运营',
						level:2,
						auth:[
							{
								id:20,
								title:'运营中心',
								children:[
									{	id:1,
										path:'3-20-1',
										title:'',
										value:0,
									},
									{
										id:2,
										path:'3-20-2',
										title:'新增',
										value:1,
									},
									{
										id:3,
										path:'3-20-3',
										title:'跟进',
										value:0,
									},
									{
										id:4,
										path:'3-20-4',
										title:'删除',
										value:0,
									}
								]
							}
						]
					}
				]
			}
		}
	},
	methods: {
		itemClick(index,i){
			uni.navigateTo({
				url:"/pages/team/editauth?index="+index+"&i="+1
			})
		},
		submit() {
			// if( this.form.username == false) return uni.$u.toast('请输入姓名');
			// if( !this.form.tel) return uni.$u.toast('请输入手机号码');
			// console.log(this.userInfo)
			var pages = getCurrentPages();
			var prevPage = pages[pages.length - 2]; //上一个页面
			console.log('6666666')
			console.log(prevPage)
			console.log('7777777')
			 //直接调用上一个页面的setData()方法，把数据存到上一个页面中去
			 // 上一个页面最后设置userdata
			 
			 prevPage.$vm.form = {name:'黎明'}
			  uni.navigateBack({//返回
					 delta: 1
			 })
		},

	}
};
</script> 

<style lang="scss" scoped>
.car_form{
	.u-form-item{
		margin: 10rpx auto;
		.u-radio-group{
			display: flex;
			flex-direction: row;
			flex-wrap: wrap;
		}
	}
}

</style>

