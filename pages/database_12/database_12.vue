<template>
	<view>
		<table-a :columns="columns" :tableData="tableData"></table-a>
	</view>
</template>

<script>
	import tableA from "@/components/table-a.vue"
	import {database12} from "../../data/projectdata.js"
	export default {
		components:{
			tableA
			
		},
		data() {
			return {
				tableData:[],
				columns:[
					{ id:1,title:'名称'},
					{ id:2,title:'珍惜度'},
					{ id:3,title:'最大所持数'},
					{ id:4,title:'买价(z)'},
					{ id:5,title:'卖价(z)'},
					{ id:6,title:'入手方法'},
					{ id:7,title:'入手可能'},
					{ id:8,title:'效果备注'},	
				]
			}
		},
		onLoad() {
			this.tableData = database12;
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
