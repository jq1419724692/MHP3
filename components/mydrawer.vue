<template>
	<view>
		<uni-drawer :visible="visible">
		    <uni-list>
				<uni-list-item   :show-arrow="false" thumb="../../static/phone/xiaomi.png" >
					<view class="phone-info">{{this.platform}} {{this.system}}</view>
					<view class="phone-info">{{model}}</view>
				</uni-list-item>
		    	<uni-list-item v-for="item in menulist" :title="item.title" :note="item.note" :show-arrow="false" :key="item.id" @click="getLists(item.method,item.url)">
					<!-- <view class="img">
						<image :src="item.pic"></image>
					</view> -->
				</uni-list-item>
		    </uni-list> 
		</uni-drawer>
	</view>
</template>

<script>
	import uniDrawer from '@/components/uni-drawer/uni-drawer.vue';
	import uniList from "@/components/uni-list/uni-list.vue";
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue";
	export default {
		props:["visible","system","platform","model","menulist"],
		components:{
			uniDrawer,
			uniList,
			uniListItem,
		},	
		data() {
			return {
				
			};
		},
		onLoad() {
			
		},
		methods:{
			getLists(methodsName){
				return this[methodsName]()
			},
			//微型数据库
			goToDatabase(){
				uni.navigateTo({
					url:"../database/database"
				})
			},
			//交流唠嗑
			joinQQGroup(){
				let key = "TZUPoe_TySU5oCDg_V9imTr0PrSjYDO3";
				plus.runtime.openURL('mqqopensdkapi://bizAgent/qm/qr?url=http%3A%2F%2Fqm.qq.com%2Fcgi-bin%2Fqm%2Fqr%3Ffrom%3Dapp%26p%3Dandroid%26k%3D'+key)
			},
			//配信任务
			goToTask(){
				uni.navigateTo({
					url:"../task/task"
				}) 
			},
			//游戏辅助
			goToAssistant(){
				uni.navigateTo({
					url:"../gameassistant/gameassistant"
				}) 
			},
			//管理存档
			file(){
				uni.navigateTo({
					url:"../managefile/managefile"
				})
			},
		}
	}
</script>

<style scoped>
   .phone-info{
		margin-left: 20rpx;
	}
	.img{
		width: 95%;
		border-radius: 30rpx;
		border: 1px solid #ff0000;
		overflow: hidden;
	}
	.img image{
		width: 100%;
		height: 250rpx;
		vertical-align: bottom;
	}
</style>

