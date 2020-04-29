<template>
	<view class="flex flex-direction pageview">
		<view class="navbar flex justify-between align-center">
			<span v-for="(item, index) in tablist" :key="index" :class="{ active: navIndex == index }">{{ item }}</span>
		</view>
		<view class="list flex-sub">
			<mescroll-uni ref="mescrollRef" @init="mescrollInit" @down="downCallback" @up="upCallback" :fixed="false">
				<order-item v-for="(item, index) in 5" :key="index"></order-item>
			</mescroll-uni>
		</view>
	</view>
</template>

<script>
import MescrollMixin from '@/components/mescroll-uni/mescroll-mixins.js';
import orderItem from '@/components/shop/order-item.vue'
export default {
	data() {
		return {
			tablist: ['待配送', '已配送', '结算中', '已完成'],
			navIndex: 0
		};
	},
	mixins: [MescrollMixin],
	components:{
		orderItem
	}
};
</script>

<style lang="scss">
.pageview,
page {
	height: 100%;
	width: 100%;
}
.navbar {
	height: 100upx;
	color: #626262;
	padding: 0 50upx;
	border-bottom: 1px solid #EAEAEA;
	font-size: 30upx;
	.active {
		color: #19a967;
		position: relative;
		&:after {
			width: 35upx;
			height: 5upx;
			background: rgba(25, 169, 103, 1);
			border-radius: 3upx;
			position: absolute;
			bottom: 0;
			left: 50%;
			transform: translateX(-50%);
		}
	}
}
.list {
	overflow: auto;
	padding-top: 20upx;
}
</style>
