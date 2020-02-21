<template>
	<view>
		<t-table>
			<t-tr>
				<t-th v-for="item in columns" :key="item.id" >{{item.title}}</t-th>
			</t-tr>
			<t-tr v-for="item in tableData" :key="item.id" fontSize="10">
				<t-td v-for="val,key,index in item" :key="index">{{ val}}</t-td>
			</t-tr>
		</t-table>
	</view>
</template>

<script>
	import tTable from "@/components/t-table/t-table.vue"
	import tTh from '@/components/t-table/t-th.vue';
	import tTr from '@/components/t-table/t-tr.vue';
	import tTd from '@/components/t-table/t-td.vue';
	export default {
		props:["columns","tableData"],
		components:{
			tTable,
			tTh,
			tTr,
			tTd
		},
		data() {
			return {
				
			};
		}
	}
</script>

<style>

</style>
