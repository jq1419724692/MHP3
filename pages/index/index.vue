<template>
	<view class="content">
		<uni-list>
			<uni-list-item v-for="item in databaselist" :title="item.title" :show-arrow="false" :key="item.id" @click="goToPage(item.url)"></uni-list-item>
		</uni-list>
		<!-- 侧滑菜单 -->
		<my-drawer :visible="visible" :model="model" :platform="platform" :system="system" :menulist="menulist"></my-drawer>
		<!-- 更多 -->
		<openAlert ref="openAlert" AlertClass="0" AlertPosition="center" :CustomPosition="CustomPosition">
			<view class="about-list">
				<view v-for="item in aboutlist" class="about-item" @click="getLists(item.method)">{{item.title}}</view>
			</view>
		</openAlert>
	</view>

</template>

<script>
	import uniList from "@/components/uni-list/uni-list.vue";
	import uniListItem from "@/components/uni-list-item/uni-list-item.vue";
	import openAlert from "@/components/open-alert/open-alert.vue";
	import BottomImageMenu from '@/components/zh-bottom-image-menu/zh-bottom-image-menu.js'
	import {databaselist,menulist,aboutlist} from "../../data/projectdata.js"
	import MyDrawer from "../../components/mydrawer.vue"
	let bottomImageMenu = null;
	export default {
		components: {
			MyDrawer,
			uniList,
			uniListItem,
			openAlert,
			BottomImageMenu
		},
		data() {
			return {
				visible: false,
				showArrow: false,
				model: "",
				system: "",
				platform: "",
				CustomPosition: {
					top: 0,
					right: 0
				},
				menulist: [],
				aboutlist: [],
				databaselist: []
			}
		},
		onLoad() {
			this.databaselist = databaselist;
			this.menulist = menulist;
			this.aboutlist = aboutlist;
			uni.getSystemInfo({
				success: (res) => {
					this.model = res.model;
					this.system = res.system;
					this.platform = res.platform.replace(res.platform[0], res.platform[0].toUpperCase());
				}
			});
			bottomImageMenu = new BottomImageMenu(this.menus);
		},
		onHide() {
			this.visible = false;
			this.$refs.openAlert.Close();
		},
		methods: {
			goToPage(url) {
				uni.navigateTo({
					url: url
				})
			},
			onNavigationBarButtonTap(val) {
				if (val.index === 0) {
					this.visible = !this.visible
				} else if (val.index === 1) {
					this.$refs.openAlert.Show();
				}
			},
			getLists(methodsName) {
				return this[methodsName]()
			},
			//加入QQ群
			joinQQGroup() {
				let key = "TZUPoe_TySU5oCDg_V9imTr0PrSjYDO3";
				plus.runtime.openURL(
					'mqqopensdkapi://bizAgent/qm/qr?url=http%3A%2F%2Fqm.qq.com%2Fcgi-bin%2Fqm%2Fqr%3Ffrom%3Dapp%26p%3Dandroid%26k%3D' +
					key)
			},
			//关于与支持
			goToAbout() {
				uni.navigateTo({
					url: "../about/about"
				})
			},
			logout() {
				plus.runtime.quit();
			},
			//一键分享
			share() {
			    bottomImageMenu.show()
			},
			//检测更新
			checkUpdate(){
				let server = "https://www.baidu.com";
				let params = {
					"appid": plus.runtime.appid,  
					"version": plus.runtime.version  
				}
				uni.request({
					url:server,
					data:params,
					success:(res)=>{
						console.log(res)
						uni.showModal({
							title:"检测更新",
							content:"检测到新版本，是否立即更新？"
						})
					}
				})
			}
				
		},
		computed: {
			menus() {
				return [{
						icon: '/static/sharemenu/wx.png',
						label: '微信好友',
						onClick() {
							uni.share({
								provider: "weixin",
								type: 1,
								scene: "WXSceneSession",
								summary: "怪物猎人p3必备辅助工具MHP3Tool最新版，下载地址：https://www.coolapk.com/game/com.sidalin.mhp3tool"
							});
							
						}
					},
					{
						icon: '/static/sharemenu/pyq.png',
						label: '朋友圈',
						onClick() {
							uni.share({
								provider: "weixin",
								type: 1,
								scene: "WXSenceTimeline",
								summary: "怪物猎人p3必备辅助工具MHP3Tool最新版，下载地址：https://www.coolapk.com/game/com.sidalin.mhp3tool"
							})
						}
					},
					{
						icon: '/static/sharemenu/qq.png',
						label: 'QQ好友',
						onClick() {
							uni.share({
								provider: "qq",
								type: 1,
								title: "怪物猎人p3必备辅助工具MHP3Tool最新版",
								href: "https://www.coolapk.com/game/com.sidalin.mhp3tool",
								summary: "怪物猎人p3必备辅助工具MHP3Tool最新版，下载地址：https://www.coolapk.com/game/com.sidalin.mhp3tool"
							})
						}
					},
					{
						icon: '/static/sharemenu/weibo.png',
						label: '新浪微博',
						onClick() {
							uni.share({
								provider: "sinaweibo",
								type: 1,
								summary: "怪物猎人p3必备辅助工具MHP3Tool最新版，下载地址：https://www.coolapk.com/game/com.sidalin.mhp3tool"
							})
						}
					},
					{
						icon: '/static/sharemenu/copy.png',
						label: '复制',
						onClick(){
							uni.setClipboardData({
								data:"怪物猎人p3必备辅助工具MHP3Tool最新版，下载地址：https://www.coolapk.com/game/com.sidalin.mhp3tool",
								
								success() {
									uni.showToast({
										title:"已复制到粘贴板",
										icon:"none"
									})
								}
							})
						}
					},
					{
						icon: '/static/sharemenu/more.png',
						label: '更多',
						onClick(){
							
						}
					}
				]
			}
		},
	}
</script>

<style>
	.about-list {
		padding: 20rpx 80rpx 20rpx;
		box-shadow: 1px 1px 5px 1px rgba(0, 0, 0, 0.2);
		line-height: 100rpx;
		background: #fff;
		font-size: 15px;
	}

	.user-info {
		position: fixed;
		left: 0;
		top: 100rpx;
	}
</style>
