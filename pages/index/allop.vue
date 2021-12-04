<template>
	<view>
		<luyj-grid-link :list="list" @gridExc="clickGrid"></luyj-grid-link>
	</view>
</template>

<script>
	export default {
		data(){
			return {
				list: [
					{
					title: '成员管理',
					cur: 'applications',
					bgColor: 'bg-blue light', // 背景颜色
					color: 'blue',
					title_show: false,
					showAll: false,
					colNumber: 3, // 显示的列数
					iconsList: [{
							cuIcon: 'group_fill',
							color: 'blue',
							name: '团队管理',
							url: '/pages/toUrl/toUrl'
						},
						{
							cuIcon: 'friendadd',
							color: 'blue',
							name: '无URL',
							exec : 'add'
						},
						{
							cuIcon: 'friendaddfill',
							color: 'blue',
							name: '无Url',
							exec: 'invite'
						}
					]
				},
				{
					title: '基础数据',
					cur: 'basic',
					bgColor: '', // 背景颜色
					color: 'blue',
					title_show: true,
					showAll: false,
					colNumber: 5, // 显示的列数
					iconsList: [{
							cuIcon: 'text',
							color: 'yellow',
							name: '基本信息',
							url: '/pages/toUrl/toUrl'
						},
						{
							cuIcon: 'peoplelist',
							color: 'blue',
							name: '员工管理',
							url: '/pages/toUrl/toUrl'
						},
		
					]
				}, {
					title: '产品目录',
					cur: 'goods',
					bgColor: '', // 背景颜色
					color: 'blue',
					title_show: true,
					showAll: false,
					colNumber: 5, // 显示的列数
					iconsList: [{
							cuIcon: 'list',
							color: 'yellow',
							name: '分类',
							url: '/pages/toUrl/toUrl'
						},
						{
							cuIcon: 'goodsnew',
							color: 'blue',
							name: '型号',
							url: '/pages/toUrl/toUrl'
						},
						{
							cuIcon: 'shake',
							color: 'olive',
							name: '设备',
							url: '/pages/toUrl/toUrl'
						},
						{
							cuIcon: 'questionfill',
							color: 'yellow',
							name: '常见问题',
							url: '/pages/toUrl/toUrl'
						}
					]
				},
				{
					title: '权限管理',
					cur: 'goods',
					bgColor: '', // 背景颜色
					color: 'blue',
					title_show: true,
					showAll: false,
					colNumber: 5, // 显示的列数
					iconsList: [{
						cuIcon: 'goodsfill',
						color: 'red',
						name: '权限设置',
						url: '/pages/toUrl/toUrl'
					}]
				}
				]
			}
		},
		onLoad() {
		}
	}
</script>

<style>
</style>
