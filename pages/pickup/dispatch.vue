<template>
	<view class="right-container">
		<uni-list
			v-for="(item, index1) in itemList"
			:key="index1" 
			:border="false"
		>
			<uni-list-item 
			:title="item['title']" 
			@click="itemClick(item)"
			link>
				<template slot="header">
					<u-checkbox-group
					            :v-model="checkboxValue1"
					            placement="column"
					            @change="checkboxChange"
					        >
					<u-checkbox
							:customStyle="{marginBottom: '8px'}"
							:label="item.title"
							:name="item.title"
						>
						</u-checkbox>
					</u-checkbox-group>
				</template>
			</uni-list-item>
		</uni-list>
	</view>
</template>

<script>
	export default{
		data(){
			return {
				checkboxValue1:[],
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
				]
			}
		},
		methods:{
			checkboxChange(){
				
			},
			itemClick(e){
				
			}
		},
		watch: {
			checkboxValue1(newValue, oldValue) {
				console.log('v-model', newValue);
			}
		},
	}
</script>

<style>
</style>
