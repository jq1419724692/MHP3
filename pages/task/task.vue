<template>
	<view>
		<uni-list>
			<uni-list-item v-for="item in tasklist" :title="item.title" :show-arrow="false" :key="item.id" ></uni-list-item>
		</uni-list>
		<!-- @click="getLists(item.method)" -->
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue";
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue";
	export default {
		components:{
			uniList,
			uniListItem
		},
		data() {
			return {
				tasklist:[
					{id:1,title:"官方配信"},
					{id:2,title:"蝴蝶效应"},
					{id:3,title:"G位任务"},
					{id:4,title:"获取更多..."}
				]
			}
		},
		methods: {
			
		}
	}
</script>

<style>

</style>
