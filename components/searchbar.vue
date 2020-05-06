<template>
	<view class="searchbar flex align-center">
		<view class="icon-list">
			<image src="/static/icon19.png" mode="widthFix"></image>
			<view>分类</view>
		</view>
		<div class="flex-sub flex align-center">
			<div class="icon">
				<image src="/static/icon21.png"></image>
			</div>
			<input class="flex-sub" v-model="keyword" placeholder="请输入你想要的产品名称" placeholder-style="color:#B4B4B4" type="text"
			 confirm-type="search" @confirm="confirm($event)" />
		</div>
		<button open-type="contact" class="contact">
			<image src="/static/icon20.png" mode="widthFix"></image>
			<view>客服</view>
		</button>
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
	.searchbar {
		padding: 14upx 0 0;
		// border: 1px solid #F3F3F3;

		image {
			width: 100%;
			height: 100%;
			display: block;
		}

		&>.flex-sub {
			height: 64upx;
			line-height: 64upx;
			font-size: 26upx;
			background: #f2f3f7;
			border-radius: 8upx;

			.icon {
				margin: 0 23upx;
				width: 31upx;
				height: 31upx;
			}

			input {
				font-size: 26upx;
			}
		}


		.icon-list,
		.contact {
			font-size: 20upx;
			text-align: center;
			background: none;
			width: 90upx;
			padding: 0;
			color: #000;

			image {
				margin: 0 auto;
				display: block;
				width: 42upx;
			}
		}

	}
</style>
