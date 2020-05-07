<template>
	<view class="cmtreply flex">
		<view class="imgbox">
			<!-- <image src="../../../static/images/news/avatar_1.jpg" class="tui-avatar"></image> -->
		</view>
		<view class="flex-sub">
			<view class="tui-nickname-box">
				<view class="tui-cmt-nickname">米兰的卡先生</view>
				<view class="tui-cmt-time">06-22 12:02</view>
			</view>
			<view class="tui-cmt-content margin-top-xs">
				<view>我一直没懂赛前问一个主教练如何评价对手的主教练， 记者究竟是想得到什么答案？☺☺☺☺☺</view>
				<view class="imglist flex flex-wrap">
					<image src="/static/demo/1.png" mode="widthFix"></image>
					<image src="/static/demo/1.png" mode="widthFix"></image>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {

			};
		}
	}
</script>

<style lang="scss">
	.cmtreply {
		text-align: left;
		line-height: 48upx;
		color: #000;
		margin-bottom:20upx;

		.imgbox {
			height: 64upx;
			width: 64upx;
			border-radius: 100%;
			overflow: hidden;
			background: #535353;
			margin-right: 25upx;
		}

		.tui-cmt-time {
			font-size: 20upx;
			color: #adadad;
			margin-top: 10upx;
			line-height: 24upx;
		}

		.imglist {
			image {
				width: 30%;
			}
		}
	}
</style>
