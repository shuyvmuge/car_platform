<template>
	<view>
		<uni-card title="标题文字" sub-title="副标题" :thumbnail="src" extra="额外信息" :is-full="true">
			<view class="btn-container">
				<u-button
					text="公里数km"
					plain
					shape="circle"
					:customStyle="customStyles"
				></u-button>
				<u-button
					text="油量"
					plain
					shape="circle"
					:customStyle="customStyles"
				></u-button>
				<u-button
					text="车况照片100"
					plain
					shape="circle"
					:customStyle="customStyles"
				></u-button>
				<u-button
					icon="edit-pen-fill"
					plain
					shape="circle"
					:customStyle="customStyles"
				></u-button>
			</view>
		</uni-card>
		<uni-card v-for="(items,indexs) in inspect" :title="items.title" :key="indexs">
			<view class="car-list"
				height="auto"
			>
				<view class="car-list-item"
					v-for="(item, index) in items.list"
					:key="index"
				>
					<view class="car-cell">
						<view class="car-cell-content">
							<view class="car-cell-title">{{item.title}}</view>
							<view class="car-cell-btn">
								<u-button
									class="u-button"
									text="正常"
									plain
									shape="circle"
									:customStyle="!item.status?carCellBtn:carCellBtned"
									@click="item.status = true"
								></u-button>
								<u-button
									class="u-button"
									text="异常"
									plain
									shape="circle"
									:customStyle="item.status?carCellBtn:carCellBtned"
									@click="item.status = false"
								></u-button>
							</view>
						</view> 
						<view v-if="item.status == false">
							<u-upload
								@afterRead="afterRead"
								@delete="deletePic"
								name="3"
								multiple
								:maxCount="10"
								:previewFullImage="true"
							></u-upload>
						</view>
					</view>
				</view>
				<u-modal
					title="请输入检查名称"
					:show="items.modal"
					closeOnClickOverlay
					@confirm="addItem(indexs)"
				>
					<u-input v-model="inspectName"></u-input>
				</u-modal>
				<view @click="items.modal = true">+添加检查项</view>
			</view>
		</uni-card>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				inspectName:'',
				src: 'https://juhe.oss-cn-hangzhou.aliyuncs.com/api_image/538/brand/2.png',
				plateNO: '粤B85D85',
				customStyles:{
					width:'auto',height:'auto',padding:'10rpx','font-size':'0.8em',
				},
				carCellBtn:{
					width:'auto',height:'auto',padding:'10rpx','font-size':'0.8em',margin:'10rpx',
				},
				carCellBtned:{
					width:'auto',height:'auto',padding:'10rpx','font-size':'0.8em',margin:'10rpx',background:'#208eff',color:'#ffffff'
				},
				inspect:[
					{
						title:'常规检查',
						modal:false,
						list:[
							{
								title:'外观',
								status:true,
								prop:'appearance'
							},
							{
								title:'内饰',
								status:true,
								prop:'Interior'
							},
							{
								title:'电器',
								status:true,
								prop:'electrical'
							}
						]
					}
				]
			}
		},
		methods:{
			addItem(indexs){
				if(this.inspectName){
					this.inspect[indexs].list.push({title:this.inspectName,status:false});
				}
				this.inspect[indexs].modal = false
			}
		}
	}
</script>

<style lang="scss">
	.btn-container{
		width: 80%;
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
		align-items: flex-start;
	}
	.car-cell-content{
		display: flex;
		justify-content: space-between;
		align-items: center;
		margin: 10rpx auto;
		.car-cell-btn{
			display: flex;
			.u-button:hover{
				color: #208eff;
			}
		}
	}
</style>
