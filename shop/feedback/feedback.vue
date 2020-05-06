<template>
	<view class="cu-list menu sm-border">
		<view class="cu-item">
			<view class="content">
				<text class="name">戴安娜玫瑰</text>
			</view>
			<view>
				<text class="state">待处理</text>
			</view>
		</view>
		<view class="cu-item">
			<view class="content flex align-start">
				<view class="title">申诉内容：</view>
				<view class="flex-sub">
					寄过来的数量不对，而且没有包装好，枝叶
					都干枯了，基本坏掉。
				</view>
			</view>

		</view>
		<view class="cu-item">
			<view class="content flex">
				<view class="title">处理意见：</view>
				<view class="flex-sub price">理赔￥9.80</view>
			</view>
		</view>
		<view class="cu-item">
			<view class="content flex">
				<view class="title">下单日期：</view>
				<view class="flex-sub">2020-02-10</view>
			</view>
		</view>
		<view class="cu-item">
			<view class="content flex">
				<view class="title">投诉日期：</view>
				<view class="flex-sub">2020-02-15</view>
			</view>
		</view>
		<view class="cu-item">
			<view class="content flex">
				<view class="title">投诉金额：</view>
				<view class="flex-sub">9.80</view>
			</view>
		</view>
		<view class="cu-item">
			<view class="content flex">
				<view class="title">处理时间：</view>
				<view class="flex-sub">2019-02-20</view>
			</view>
		</view>
		<view class="cu-item">
			<view class="content">
				<view class="title">实物图片：</view>
				<view class="imgbox">
					<image src="/static/demo/3.png" mode="widthFix"></image>
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
	.name {
		font-size: 32upx;
		color: #FD3C3E;
	}

	.state {
		color: #FF9518;
		font-size: 30upx;
	}

	.price {
		color: #FD3C3E;
		font-size: 30upx;
	}

	.cu-list {
		color: #7C7C7C;
		font-size: 28upx;

		.cu-item {
			.content {
				padding: 40upx 0;
			}
		}

		.title {
			color: #333;
			font-weight: bold;
			min-width: calc(4em + 15px);
		}
		.imgbox{
			width: 100%;
			margin-top: 30upx;
			box-shadow: 0 10upx 10upx rgba(0,0,0,.1);
			border-radius:12upx;
			overflow: hidden;
			image{
				width: 100%;
			}
		}
	}
</style>
