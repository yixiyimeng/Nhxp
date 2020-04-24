<template>
	<view class="pageview flex flex-direction">
		<image src="/static/shop/wallet.png" mode="widthFix" class="bg"></image>
		<cu-custom :bgColor="bgColor" :isBack="true">
			<block slot="content">我的钱包</block>
		</cu-custom>
		<view class="main">
			<view class="walletinfo">
				<view>账户余额(元)</view>
				<view class="price">43476.88</view>
				<navigator url="/shop/cashoutlist/cashoutlist" class="link">提现记录</navigator>
				<view class="nav flex align-center justify-center">
					<view class="flex-sub">
						<view>本月收入</view>
						<view class="price">12688.05</view>
					</view>
					<span class="line"></span>
					<view class="flex-sub">
						<view>累计收入</view>
						<view class="price">12688.05</view>
					</view>
				</view>
				<navigator class="btn" url="/shop/applycashout/applycashout">提现</navigator>
			</view>
			<view class="list">
				<view class="flex justify-between">
					<span>结算中</span>
					<span class="price">476.88</span>
				</view>
				<view class="flex justify-between">
					<span>已提现</span>
					<span class="price">476.88</span>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				bgColor: 'nobg'
			};
		}
	};
</script>

<style lang="scss">
	page {
		height: 100%;
		background: #fff;
	}

	.bg {
		width: 100%;
		position: absolute;
		z-index: 0;
		top: 0;

	}

	.main {
		position: relative;
		z-index: 999;
	}

	.walletinfo {
		position: relative;
		text-align: center;
		color: #585858;
		font-size: 28upx;
		background: #fff;
		box-shadow: 0 2upx 6upx 0px rgba(26, 170, 104, 0.27);
		border-radius: 12upx;
		margin: 30upx;
		padding: 50upx 0;

		.price {
			color: #2E302F;
			font-size: 56upx;
			margin-top: 27upx;
		}

		.link {
			position: absolute;
			display: block;
			color: #989898;
			font-size: 26upx;
			width: 145upx;
			line-height: 55upx;
			background: rgba(239, 239, 239, 1);
			border-radius: 28upx;
			top: 24upx;
			right: 24upx;
		}

		.nav {
			color: #848484;
			font-size: 26upx;
			margin-top: 65upx;

			.price {
				font-size: 50upx;
				margin-top: 20upx;
			}

			.line {
				width: 2upx;
				height: 100upx;
				background: #EDEDED;
				display: block;
			}
		}

		.btn {
			width: 580upx;
			line-height: 100upx;
			background: rgba(25, 169, 103, 1);
			box-shadow: 0px 9upx 27upx 0px rgba(25, 169, 103, 0.58);
			border-radius: 12upx;
			margin: 47upx auto 0;
			color: #fff;
			font-size: 30upx;
		}
	}
	.list{
		margin: 0 30upx;
		&>view{
			padding: 32upx 0;
			font-size: 30upx;
			color: #333;
			border-bottom: 1px solid #EAEAEA;
			.price{
				color: #C2C2C2;
				font-size: 36upx;
			}
		}
	}
</style>
