<template>
	<view class="searchbar flex align-center">
		<div class="flex-sub flex align-center">
			<div class="icon">
				<image src="/static/search@2x.png"></image>
			</div>
			<input class="flex-sub" v-model="keyword" placeholder="请输入你想要的产品名称" placeholder-style="color:#B4B4B4" type="text" confirm-type="search" @confirm="confirm($event)" />
		</div>
		<button open-type="contact" class="contact">
			<image src="/static/customer_service@2x.png" mode="widthFix"></image>
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
		padding: 14upx 30upx;
		border: 1px solid #F3F3F3;

		image {
			width: 100%;
			height: 100%;
			display: block;
		}

		&>.flex-sub {
			height: 64upx;
			line-height: 64upx;
			font-size: 26upx;
			background: #F7F7F7;
			border-radius: 32upx;

			.icon {
				margin: 0 23upx;
				width: 31upx;
				height: 31upx;
			}
			input{
				font-size: 26upx;
			}
		}

		.contact {
			margin-left: 29upx;
			height: 44upx;
			width: 44upx;
			display: block;
			padding: 0;
			background: none;

		}
	}
</style>
