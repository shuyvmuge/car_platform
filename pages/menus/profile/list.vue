<template>
	<view class="profile-list">
		<view class="condition">
			<car-filter-button :filters="filters" width="20%" @click="filterAction"></car-filter-button>
			<!-- 类型 -->
			<u-action-sheet
				cancelText="取消" 
				:actions="types"
				 @select="typeAction" 
				 @close="typeShow = false" 
				 title="选择类型"
				 :show="typeShow"
			></u-action-sheet>
			<!-- 日期 -->
			<u-datetime-picker
				:show="dateShow"
				v-model="date"
				:minDate="1420686689000"
				:maxDate="1786778555000"
				mode="year-month"
				@confirm="dateConfirm"
			></u-datetime-picker>
			<!-- 操作人 -->
			<u-action-sheet
				cancelText="取消" 
				:actions="operators"
				 @select="opAction" 
				 @close="opShow = false" 
				 title="选择类型"
				 :show="opShow"
			></u-action-sheet>
		</view>
		<view class="content">
			<uni-list :border="false">
				 <car-list-item 
					:border="false"
					:thumb="item.logo"
					thumbSize="lg"
					v-for="(item,index) in list"
					:note="item.create_time"
					:key="index"
					:title="item.plate" 
					:showArrow="true"
					:rightText="item.username"
				>
				</car-list-item>
			</uni-list>
			<u-loadmore :status="status"/>
		</view>
	</view>
</template>

<script>
	export default{
		onReachBottom() {
			if(this.page >= 3){
				this.status = 'nomore';
				return ;
			}
			this.status = 'loading';
			this.page = ++ this.page;
			setTimeout(() => {
				for (let i=0;i<15;i++) {
					this.list.push({
						id:1,
						plate:'粤Y458645',
						username:'李四',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					})
				}
			}, 2000)
		},
		methods:{
			filterAction(e){
				console.log(e.actionName)
				switch(e.actionName){
					case 'date':
						this.dateShow = true;
						break;
					case 'type':
						this.typeShow = true;
						break;
					case 'operator':
						this.opShow = true;
						break;
				}
			},
			typeAction(e){
				this.filters.type.title = e.name
				console.log(e)
			},
			dateConfirm(e){
				this.dateShow = false
				this.filters.date.title = uni.$u.timeFormat(e.value, 'yyyy-mm');
				console.log(e)
			},
			opAction(e){
				this.filters.operator.title = e.name
			},
			selectFilter(e){
				console.log(e)
			}
		},
		data(){
			return{
				date:Number(new Date()),
				typeShow:false,
				opShow:false,
				dateShow:false,
				status: 'loadmore',
				page: 0,
				filters:{
					type:{
						title:'类型',
						actionName:'type',
					},
					date:{
						title:'月份',
						actionName:'date',
					},
					operator:{
						title:'操作人',
						actionName:'operator',
						
					}
				},
				/* replace */
				types:[
					{
						name:'手机',
					},
					{
						name:'vin码',
					},
					{
						name:'驾驶证',
					}
				],
				/* replace */
				operators:[
					{
						name:'张三',
					},
					{
						name:'李四',
					},
					{
						name:'王五',
					}
				],
				/* replace */
				list:[
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					},
					{
						id:1,
						plate:'粤Y458645',
						username:'张三',
						create_time:'2022-11-15',
						logo:'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png'
					}
				]
			}
		}
	}
</script>

<style lang="scss" scoped>
	.content{
		padding-top: 160rpx;
	}
</style>
