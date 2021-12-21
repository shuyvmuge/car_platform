<template>
	<view class="right-container">
		<uni-table class="table" @selection-change="selectChange" border stripe emptyText="暂无更多数据" type="selection" >
			<uni-tr>
				<uni-th>施工人员</uni-th>
				<uni-th>销售人员</uni-th>
				<uni-th>质检人员</uni-th>
			</uni-tr>
		    <uni-tr v-for="(item,index) in itemList" :key="index" :value="item">
		        <uni-td>{{item.title}}</uni-td>
		        <uni-td></uni-td>
		        <uni-td></uni-td>
		    </uni-tr>
		</uni-table>
		
		<u-popup :show="dsheet" @close="close" @open="open">
			<view>
				<text>出淤泥而不染，濯清涟而不妖</text>
			</view>
		</u-popup>
		
		<view class="btn-area">
			<button class="mini-btn" type="default" size="mini">质检</button>
            <button class="mini-btn" type="default" size="mini">销售</button>
            <button class="mini-btn" type="default" size="mini" @click="dsheet = true">施工</button>
		</view>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				checkboxValue1:[],
				dsheet:true,
				itemList:[
					{
						id:1,
						title:'机油',
						cate:'配件',
						name:'jiyou'
					},
					{
						id:2,
						title:'换机油',
						cate:'工时',
						name:'hjy'
					}
				],
				userGroup:[
					{
						gid:1,
						title:'质检',
						users:[
							{
								id:1,
								name:'张三',
							},{
								id:2,
								name:'李四',
							},
						]
					},
					{
						gid:1,
						title:'机修',
						users:[
							{
								id:1,
								name:'王五',
							},{
								id:2,
								name:'麻二',
							},
						]
					}
				]
			}
		},
		methods:{
			itemClick(e){
				
			},
			selectChange(e){
				var that = this
				console.log(e)
				e.detail.index.forEach(function(i,l){  
				   // console.log(that.itemList[i])
				});
			}
		},
		
	}
</script>

<style lang="scss" scoped>
	.right-container{
		width: 100%;
		.table{
			width: 100%;
		}
		.btn-area{
			width: 100%;
			position: fixed;
			bottom: 0;
			.mini-btn{
				margin: 30rpx;
				float: right;
			}
		}
	}
</style>
