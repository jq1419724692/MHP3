<template>
	<view>
		<view class="studio">
			<view class="img">
				<image src="../../static/timi.png" ></image>
				<view class="copyright">
					<text>Copyright &copy; 2019 TiMi S1 Studio</text>
				</view>
			</view>
		</view>
		<uni-list>
			<uni-list-item v-for="item in aboutlist" :title="item.title"  :show-arrow="item.showArrow" :key="item.id" @click="getList(item.methods)"></uni-list-item>
		</uni-list>	
	</view>
</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue";
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue";
	
	export default {
		components:{
			uniList,
			uniListItem,
			
		},
		data() {
			return {
				aboutlist:[
					{id:1,title:"关于制作",methods:"about"},
					{id:1,title:"访问官网",methods:"goToOfficalWeb"},
					{id:1,title:"支持捐助",methods:"donate"},
					{id:1,title:"交流QQ群",methods:"joinQQGroup"},
					{id:1,title:"反馈建议",methods:"feedback"}
				]
				
			}
		},
		methods: {
			getList(methodsName){
				return this[methodsName]()
			},
			goToOfficalWeb(){
				plus.runtime.openURL("http://ruanxin.52emu.cn/")
			},
			joinQQGroup(){
				let key = "TZUPoe_TySU5oCDg_V9imTr0PrSjYDO3";
				plus.runtime.openURL("mqqopensdkapi://bizAgent/qm/qr?url=http%3A%2F%2Fqm.qq.com%2Fcgi-bin%2Fqm%2Fqr%3Ffrom%3Dapp%26p%3Dandroid%26k%3D" + key);	
			},
			feedback(){
				uni.share({
					provider: "mail",
					
					type: 1,
					summary: "怪物猎人p3必备辅助工具MHP3Tool最新版，下载地址：https://www.coolapk.com/game/com.sidalin.mhp3tool",			
				})
			},
			donate(){
				uni.showModal({
					title:"黑炎剑姬：",
					content:"大家好，我是剑姬。我本人也是一位萌新猎人。很感谢大家一直以来的支持与鼓励，剑姬就算不吃不喝不睡觉也要继续战斗下去，做做好的游戏辅助软件，。如果有能力的朋友，欢迎请剑姬喝杯奶茶，来份外卖，就当作对服务器的支持，剑姬感激不尽。没能力的朋友，也不勉强，有这份心意，剑姬就万分感谢了，最后不管有没有打赏，剑姬都感谢大家一直以来的陪伴，剑姬真心感谢，我爱你们( ˘ ³˘)♡",
					confirmText:"点击继续",
					cancelText:"残忍离开",
					success(){
						uni.showModal({
							title:"满怀期待的目光",
							content:'123456'
						})
							
						
					}
				})
			},
			about(){
				uni.showModal({
					title:"特别鸣谢",
					showCancel:false,
					content:"132456789"
				})
			}
		}
	}
</script>

<style>
.studio{
	width: 100%;
	text-align: center;
	height: 400rpx;
}
.copyright{
	font-size: 30rpx;
	color: #808080;
}
.img{
	margin: 100rpx auto;
}
.img image{
	width: 200rpx;
	height: 200rpx;
}
</style>
