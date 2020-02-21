<template>
	<view >
		<uni-list>
			<uni-list-item v-for="item in databaselist" :title="item.title" :show-arrow="false" :key="item.id" @click="goToPage(item.url)"></uni-list-item>
		</uni-list>
		
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue";
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue";
	import {databaselist} from "../../data/projectdata.js"
	export default {
		components:{
			uniList,
			uniListItem,
		},
		data() {
			return {
				databaselist:[]
			}
		},
		onLoad() {
			this.databaselist = databaselist;
		},
		methods: {
			goToPage(url){
				uni.navigateTo({
					url:url
				})
			}
		}
	}
</script>

<style>

</style>
