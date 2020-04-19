<template>
	<view class="pageview ">
	<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
		<evaluate-item v-for="(item, index) in 10" :key="index" :goodsinfo="item"></evaluate-item>
	</mescroll-uni>
	</view>
</template>

<script>
	import MescrollUni from '@/components/mescroll-uni/mescroll-uni.vue';
	import evaluateItem from '@/components/shop/evaluateItem.vue';
	export default {
		data() {
			return {
				menulist: ['全部', '玫瑰', '百合', '康乃馨', '梅花', '牡丹'],
				downOption: {
					use: true,
					auto: false //是否在初始化后,自动执行下拉回调callback; 默认true
				},
				upOption: {
					noMoreSize: 1,
					page: {
						num: 0,
						size: 10
					},
				},
				mescroll: null, //mescroll实例对象

			};
		},
		components: {
			MescrollUni,
			evaluateItem
		},
		methods: {
			mescrollInit(mescroll) {
				this.mescroll = mescroll;
			},
			/*下拉刷新的回调, 有三种处理方式: */
			downCallback(mescroll) {
				mescroll.resetUpScroll(); // 重置列表为第一页 (自动执行 page.num=1, 再触发upCallback方法 )
			},
			/*上拉加载的回调*/
			upCallback(mescroll) {

			},

		}
	}
</script>

<style lang="scss">
	.pageview {
		height: 100%;overflow: auto;
	}

	
</style>
