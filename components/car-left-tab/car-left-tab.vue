<template>
	<view class="car-left-tab">
		<view class="left">
			<scroll-view 
				:scroll-with-animation="true"
				scroll-y 
				:style="`height:${ height }px`"
			>
				<view 
					class="left-item" 
					v-for="(item,index) in list" 
					:key="index"
					:class="{'left-item-active': index == active }"
					@click="categoryClick(item, index)"
				>
					<view class="left-item-icon" v-if="index == active"></view>
					<view class="left-item-title"> {{ item.name }}</view>
				</view>
			</scroll-view>
		</view>
		<view class="right">
			<scroll-view scroll-y
				@scroll="scroll" 
				:style="`height: ${ height }px`" 
				scroll-with-animation
				:scroll-into-view="cIndex"
			>
				<view class="right-container" v-for="(item,index) in list" :key="index">
					<uni-list
						v-show="index == active"
						v-for="(child, index1) in item.children"
						:key="index1" 
						:border="false"
					>
						<uni-list-item 
						:title="child['name']" 
						:note="child['date']" 
						@click="itemClick(item, child)"
						link>
							<template slot="header">
								<image class="slot-image" :src="child['img']" mode="widthFix"></image>
							</template>
						</uni-list-item>
					</uni-list>
				</view>
			</scroll-view>
		</view>
	</view>
</template>

<script>
	export default {
		name: "CarLeftTab",
		data() {
			return {
				height: 0,
				active: 0,
				cIndex: '',
				topList: [],
				flag: false
			}
		},
		props: {
			list: {
				type: Array,
				default: () => {
					return []
				}
			},
			maxSelected: {
				type: [String, Number],
				default: '-1'
			}
		},
		methods: {
			scroll(e) {
				if(this.flag){
					this.flag = false
					return
				}
				let scrollTop = e.target.scrollTop
				for(let i = 0;i < this.topList.length; i++){
					let h1 = this.topList[i]
					let h2 = this.topList[i + 1]
					if(scrollTop > h1 && scrollTop < h2) {
						this.active = i
					}
				}
			},
			categoryClick(category, index) {
				this.$nextTick(() => {
					this.cIndex = `cid${ category.id }`
					this.flag = true
				})
				this.cIndex = ''
				this.active = index;
			},
			itemClick (category, item) {
				uni.navigateTo({
					url:'/pages/pickup/detail?id='+item.id
				})
				console.log('itemClick')
			},
			getValues () {
				let ids = []
				this.list.forEach(item => {
					ids = ids.concat(Object.values(item.selectedIds))
				})
				return ids
			},
			getActive () {
				return { index: this.active, data: JSON.parse(JSON.stringify(this.list[this.active])) }
			},
			getSelectedCount () {
				let ids = this.getValues()
				this.$emit('change', JSON.parse(JSON.stringify(ids)))
			},
			getNodesInfo () {
				const query = uni.createSelectorQuery().in(this);
				query.selectAll('.category-name').boundingClientRect().exec(res=>{
					let nodes = res[0]
					this.topList =  nodes.map(item => item.top)
				})
			},
			/* scrollToBottom () {
				setTimeout(()=>{
					this.active = this.active + 1
				}, 50)
			}, */
			reload () {
				this.getNodesInfo()
			}
		},
		mounted() {
			uni.getSystemInfo({
				success: res => {
					this.height = res.windowHeight - 24;
				}
			})
			this.getNodesInfo()
			setTimeout(() => {
				this.getSelectedCount()
			}, 500)
		}
	}
</script>

<style lang="less" scoped>
	page{
		padding-bottom: 0;
	}
	.car-left-tab {
		display: flex;
		width: 100%;
		// flex-wrap: wrap;
	}

	.left {
		width: 20%;
		background: #f8f8f8;
	}

	.left-item {
		font-size: 28rpx;
		color: #333333;
		display: flex;
		align-items: center;
		justify-content: flex-start;
		padding: 40rpx 30rpx;
		.left-item-icon{
			background-color: #208eff;
			width: 5px;
			height: 14px;
			margin-right: 20rpx;
		}
	}
	
	.left-item-active {
		background: #FFFFFF;
		color: #208eff;
		font-weight: bold;
		padding-left: 0;
	}
	
	.right {
		width: 75%;
		background: #FFFFFF;
	}
	
	.right-container {
		width: 100%;
		.slot-image{
			width: 120rpx;
			height: 120rpx;
		}
		
	}

	.right-item {
		margin-left: 32rpx;
		margin-bottom: 42rpx;
		width: 100%;
		height: 72rpx;
		line-height: 72rpx;
		background: #FFFFFF;
		border: 2rpx solid #338B61;
		opacity: 1;
		border-radius: 16rpx;
		font-size: 28rpx;
		text-align: center;
		color: #338B61;
		font-weight: bold;
	}


	.right-item image {
		width: 50px;
		height: 50px;
	}

	.active {
		color: #F24544;
	}

	.padding {
		height: var(--status-bar-height);
		width: 100%;
		top: 0;
		position: fixed;
		background-color: #F24544;
	}
</style>
