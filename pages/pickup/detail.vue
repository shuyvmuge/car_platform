<template>
	<view class="car_detail">
		<view class="car_header">
			<uni-card 
				title="苏B99999" 
				sub-title="王总 18898875042" 
				:thumbnail="src" 
				padding="30rpx 0 100rpx 10rpx"
				:is-full="true"
				>
				<view class="btn-detail-container">
					<u-button
						v-for="(item,index) in carAction"
						:key="index"
						:text="item.name"
						:icon="item.icon"
						:plain="true"
						shape="circle"
						:customStyle="customBtnStyle"
						@click="carActionClicked(item.actionName)"
					></u-button>
				</view>
			</uni-card>
		</view>
		
		<car-group :title="WOActions.title" mode="card">
			<car-card 
			class="uni-card" 
			title="美容 $99" 
			sub-title="2012-10-12 18:36:30"  
			:thumbnail="src" 
			spacing="0"
			:is-full="true"
			>
				<view class="btn-order-container">
					<u-button
						v-for="(item,index) in WOActions.itemList"
						:key="index"
						class="action"
						:text="item.name"
						plain
						shape="circle"
						:customStyle="customBtnStyle"
						@click="actionClicked(item.actionName)"
					></u-button>
				</view>
			</car-card>
			<u-action-sheet
				cancelText="取消" 
				:actions="WOActions.itemList[0].items"
				 @select="selectMore" 
				 @close="moreActionShow = false" 
				 :title="WOActions.itemList[0].name"
				 :show="moreActionShow"
			></u-action-sheet>
		</car-group>
		
		<car-group :title="CustomerData.title" mode="card">
			<car-grid-board 
				@setClick="boardDataSet" 
				@linkClick="boardDataTo" 
				:list="CustomerData.itemList"
			></car-grid-board>
		</car-group>

		<car-group :title="saleHelp.title" mode="card">
			<uni-list :border="false">
				<uni-list-item 
				v-for="(item,index) in saleHelp.itemList"
				:key="index"
				:border="false"
				:title="item.name" 
				:note="item.note" 
				@click="saleHelpClicked(item.actionName)"
				link>
				<template slot="header">
					<u-icon size="22" :name="item.icon"></u-icon>
				</template>
				</uni-list-item>
			</uni-list>
		</car-group>
	
	</view>
</template>

<script>
	export default{
		data(){
			return {
				moreActionShow: false,
				src: 'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png',
				customBtnStyle:{
					width:'auto',
					height:'auto',
					padding:'10rpx 20rpx',
					fontSize:'0.8em',
					margin:'auto 15rpx',
					color:'#3a3a3a'
				},
				carAction:[
					{
						id:1,
						actionName:'consume',
						name:'消费',
						icon: 'rmb-circle'
					},
					{
						id:2,
						actionName:'call',
						name:'电话',
						icon: 'phone'
					},
					{
						id:3,
						actionName:'cardata',
						name:'资料',
						icon:'edit-pen'
					},
					{
						id:4,
						actionName:'member',
						name:'会员',
						icon:'account'
					}
				],
				WOActions:{
					title:'在线工单',
					itemList:[
						{
							id:1,
							actionName:'moreAction',
							name:'更多操作',
							items: [
								{
									id:1,
									actionName:'dispatch',
									name:'派工'
								},
								{
									id:2,
									actionName:'deposit',
									name:'收定金'
								},
								{
									id:3,
									actionName:'cancel',
									name:'取消工单'
								},
								{
									id:4,
									actionName:'quality',
									name:'完工质检'
								},
								{
									id:5,
									actionName:'construction',
									name:'透明施工'
								},
							]
						},
						{
							id:2,
							actionName:'discount',
							name:'打折'
						},
						{
							id:3,
							actionName:'changePrice',
							name:'改价'
						},
						{
							id:4,
							actionName:'pay',
							name:'支付'
						}
					]
				},

				CustomerData: {
					title:'客户运营',
					itemList:[
						{
							id:1,
							title:'刹车片',
							button:{
								text:'设置'
							}
						},
						{
							id:2,
							title:'机油',
							link:{
								text:'已过期',
								note:'2021-06-24'
							}
						},
						{
							id:3,
							title:'保险',
							button:{
								text:'设置'
							}
						},
						{
							id:4,
							title:'波箱油',
							button:{
								text:'设置'
							}
						},
						{
							id:5,
							title:'轮胎',
							button:{
								text:'设置'
							}
						},
						{
							id:6,
							title:'刹车油',
							button:{
								text:'设置'
							}
						},
						{
							id:7,
							title:'美容',
							button:{
								text:'设置'
							}
						},
						{
							id:8,
							title:'其他',
							button:{
								text:'设置'
							}
						}
					]
				},
				
				saleHelp:{
					title:'销售助手',
					itemList:[
						{
							id:1,
							actionName:'follow',
							icon:'chat',
							name:'关注微信',
							note:'关注微信公众号，及时获得消费通知'
						},
						{
							id:2,
							actionName:'cardata',
							icon:'edit-pen',
							name:'需完善资料',
							note:'便于后期销售和业务跟踪'
						},
					]
				},
			}
		},
		methods:{
			carActionClicked(actionName){
				switch(actionName){
					case 'call':
					uni.makePhoneCall({
					    phoneNumber: '15898875042' 
					});
				}
			},
			actionClicked(actionName){
				switch(actionName){
					case 'moreAction':
					this.moreActionShow = true
				}
			},
			selectMore(e){
				console.log(e)
				uni.navigateTo({
					url:e.url
				})
			},
			boardDataSet(e){
				console.log(e)
			},
			boardDataTo(e){
				console.log(e)
			}
		},
		onLoad() {
			
		}
	}
</script>

<style lang="scss">
	.car_header{
		.btn-detail-container{
			display: flex;
			flex-direction: row;
			justify-content: flex-start;
			align-items: flex-start;
		}
	}
	.btn-order-container{
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: flex-end;
		align-items: center;
	}
	
</style>
