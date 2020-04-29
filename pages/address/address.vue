<template>
	<view class="flex flex-direction pageview">
		<view class="list flex-sub">
			<mescroll-uni ref="mescrollRef" @init="mescrollInit" @down="downCallback" @up="upCallback" :fixed="false">
				<address-item v-for="(item,index) in 5" :key="index"></address-item>
			</mescroll-uni>

		</view>
		<view class="addbtn bg-white">+ 新增收货地址</view>
	</view>
</template>

<script>
	import addressItem from '@/components/address-item.vue'
	export default {
		data() {
			return {

			};
		},
		components: {
			addressItem
		},
		methods: {}
	}
</script>

<style lang="scss">
	page,
	.pageview {
		height: 100%;
		width: 100%;
		background: #f0f0f0;
		overflow: hidden;
		.list{
			overflow: auto;
			padding:30upx 0;
		}
		.addbtn{
			font-size: 26upx;
			color: #000;
			line-height: 120upx;
			text-align: center;
			border-top: 1px solid #c9c9c9;
		}
	}
</style>
