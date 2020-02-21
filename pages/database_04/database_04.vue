<template>
	<view>
		<table-a :columns="columns" :tableData="tableData"></table-a>
	</view>
</template>

<script>
	import tableA from "@/components/table-a.vue"
	import {
		database04
	} from "../../data/projectdata.js"
	export default {
		components: {
			tableA

		},
		data() {
			return {
				tableData: [],
				columns: [{
						id: 1,
						title: 'No.'
					},
					{
						id: 2,
						title: '技能名称'
					},
					{
						id: 3,
						title: '技能效果'
					},
					{
						id: 4,
						title: '记忆力'
					},
					{
						id: 5,
						title: '所需点数（pts）'
					},
					{
						id: 6,
						title: '备注'
					},

				]
			}
		},
		onLoad() {
			this.tableData = database04;
		},
		methods: {

		}
	}
</script>

<style>

</style>
