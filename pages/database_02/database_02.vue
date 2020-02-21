<template>
	<view>
		 <table-a :columns="columns" :tableData="tableData"></table-a>
	</view>
</template>

<script>
	import tableA from "@/components/table-a.vue"
	import {database02} from "../../data/projectdata.js"
	export default {
		components:{
			tableA
			
		},
		data() {
			return {
				tableData:[],
				columns:[
					{ id:1,title:'No.'},
					{ id:2,title:'调合结果'},
					{ id:3,title:'素材1'},
					{ id:4,title:'素材2'},
					{ id:5,title:'成功率'},
					{ id:6,title:'个数'},
				]
			}
		},
		onLoad() {
			this.tableData = database02;
		},
		methods: {
			
		}
	}
</script>

<style>
</style>