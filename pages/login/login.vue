<template>
	<view class="flex flex-direction pageview">
		<view class="group flex-sub">
			<view class="row flex">
				<input type="text" placeholder="请输入手机号码" class="flex-sub">
			</view>
			<view class="row flex">
				<input type="text" placeholder="请输入验证码" class="flex-sub">
				<view class="getcode">获取验证码</view>
			</view>
			<view class="defaultBtn margin-top-lg">登录</view>
			<view class="text-orange text-right margin-top">收不到验证码？</view>
		</view>
		<view class="otherway">
			<view class="title flex align-center">
				<view class="line flex-sub"></view>
				<view>第三方账号登录</view>
				<view class="line flex-sub"></view>
			</view>
			<view class="wechat">
				<image src="../../static/wechat.png" mode="widthFix"></image>
				<view>微信登录</view>
			</view>
			<view class="tag margin-top margin-bottom-lg">
				登录即代表你同意 <navigator url="" class="text-orange">《服务协议》</navigator>
				和<navigator url="" class="text-orange">《隐私政策》</navigator>
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
	page,
	.pageview {
		height: 100%;
		width: 100%;
	}

	.group {
		margin: 0 30upx;
		font-size: 26upx;

		.row {
			border-bottom: 1px solid #e5e5e5;
			margin: 0 15upx;
			padding: 25upx 20upx;

			.getcode {
				color: #fff;
				width: 165upx;
				height: 60upx;
				line-height: 60upx;
				text-align: center;
				border-radius: 20upx;
				background-image: linear-gradient(90deg, #fa9649, #fc713a);
			}
		}
	}

	.otherway {
		text-align: center;
		font-size: 26upx;
		color: #878787;

		.title {
			margin: 0 30upx;
			font-weight: bold;

			.line {
				height: 1px;
				background: #e5e5e5;
			}

			&>view:nth-child(2) {
				margin: 0 30upx;
			}
		}

		image {
			display: block;
			margin: 35upx auto 25upx;
			width: 116upx;
		}

		navigator {
			display: inline-block;
		}
	}
</style>
