<template>
	<view class="flex flex-direction pageview">
		<app-tabs v-model="tabIndex" :tabs="tabs" @change="tabChange"></app-tabs>
		<view class="main flex-sub">
			<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
				<view class="list">
					<favgoods v-for="(item,index) in 20" :key="index" v-if="tabIndex==0"></favgoods>
					<favshop v-for="(item,index) in 20" :key="index" v-if="tabIndex==1"></favshop>
				</view>
			</mescroll-uni>
		</view>

	</view>
</template>

<script>
	import AppTabs from "@/components/app-tabs.vue";
	import favgoods from "@/components/favgoods.vue";
	import favshop from "@/components/favshop.vue";
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js"
	export default {
		data() {
			return {
				tabIndex: 1,
				tabs: ['产品', '店铺']
			};
		},
		mixins: [MescrollMixin],
		components: {
			AppTabs,
			favgoods,
			favshop
		},
		methods: {
			tabChange() {

			}
		}
	}
</script>

<style lang="scss">
	page,
	.pageview {
		height: 100%;
		width: 100%;
		background: #f0f0f0;
		overflow: hidden;

		.tabbar {
			box-shadow: 0 -5upx 5upx rgba(0, 0, 0, .1);
		}

		.list {
			padding: 0 25upx 20upx;
			.goodsinfo,.shopinfo {
				margin-bottom: 20upx;
			}
			
		}
		.main{
			overflow: auto;
			margin-top: 20upx;
		}
	}
</style>
