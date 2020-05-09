<template>
	<view class="flex flex-direction pageview">
		<view class="flex justify-between reply-hd align-center">
			<view class="flex align-center">
				<text class="title">购买评价</text>
				<tui-rate :current="index" @change="change" :size="14" active='#fc743c'></tui-rate>
				<text class="num">4.0</text>
			</view>
			<text>共有1002条评论</text>
		</view>
		<view class="flex-sub main">
			<mescroll-uni :down="downOption" @down="downCallback" :up="upOption" @up="upCallback" @init="mescrollInit" :fixed="false">
				<view class="list">
					<cmt-reply v-for="(item,index) in 20" :key="index"></cmt-reply>
				</view>
			</mescroll-uni>
		</view>
	</view>
</template>

<script>
	import tuiRate from "@/components/rate/rate"
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js"
	import cmtReply from "@/components/cmt-reply"
	export default {
		data() {
			return {
				index: 4
			};
		},
		mixins: [MescrollMixin],
		components: {
			tuiRate,
			cmtReply
		},
		methods: {
			change() {
			}
		}
	}
</script>

<style lang="scss">
	.pageview,
	page {
		height: 100%;
		width: 100%;
		overflow: hidden;

		.reply-hd {
			color: #8e8e8d;
			padding: 0 60upx;
			height: 140upx;
			font-size: 22upx;
			border-bottom: 1px solid #eee;

			.title {
				color: #000;
				font-size: 28upx;
				margin-right: 30upx;
			}

			.num {
				color: #fc743c;
				margin-left: 30upx;
			}
		}

		.main {
			overflow: auto;

			.list {
				.cmtreply {
					padding: 10upx 40upx;
					border-bottom: 1px solid #eee;
				}
			}
		}
	}
</style>
