<template>
	<view class="account">
		<image src="../../static/money.png" mode="widthFix"></image>
		<view>账户余额</view>
		<view class="price">￥8888.00</view>
		<navigator class="submitBtn" url="/pages/accountDetails/accountDetails">账户明细</navigator>
		<navigator class="cancelBtn margin-top" url="/pages/applycashout/applycashout">提现</navigator>
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
	.account {
		text-align: center;
		padding-top: 150upx;
		font-size: 30upx;
		margin: 0 25upx;
		color: #000;

		image {
			display: block;
			width: 92upx;
			margin: 0 auto 50upx;
		}
		.price{
			font-size: 60upx;
			font-weight: blod;
			margin-top: 10upx;
			margin-bottom: 150upx;
		}
	}
</style>
