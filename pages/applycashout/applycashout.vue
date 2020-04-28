<template>
	<view class="group">
		<view class="row">
			<view class="title flex justify-between">
				<view class="action">提现金额</view>
				<view>请输入提现金额</view>
			</view>
			<view class="row-text flex justify-between align-center">
				<input type="text" value="" placeholder="最小提现额度为10元" class="flex-sub" />
				<view class="text-orange">全部提现</view>
			</view>

		</view>
		<view class="title solid-bottom">
			<view class="action">
				提现手续费为：0.7%（0元）
			</view>
		</view>
		<view class="title solid-bottom">
			<view class="action">最终到账金额：0元</view>
		</view>
		<radio-group class="block margin-top" @change="RadioChange">
			<view class="checkgroup flex justify-center">
				<view class="radio-item">
					<radio class="orange" :class="waytype=='alipay'?'checked':''" :checked="waytype=='alipay'?true:false" value="alipay"></radio>
					<span>支付宝</span>
				</view>
				<view class="radio-item">
					<radio class="orange" :class="waytype=='bank'?'checked':''" :checked="waytype=='bank'?true:false" value="bank"></radio>
					<span>银行卡</span>
				</view>
				<view class="radio-item">
					<radio class="orange" :class="waytype=='wechat'?'checked':''" :checked="waytype=='wechat'?true:false" value="wechat"></radio>
					<span>其他</span>
				</view>
			</view>
		</radio-group>
		<view class="tab-item" v-if="waytype=='alipay'">
			<view class="row">
				<view class="title flex justify-between">
					<view class="action">支付宝账户：</view>
				</view>
				<view class="row-text flex justify-between align-center">
					<input type="text" value="" placeholder="请输入支付宝账户" class="flex-sub" />
				</view>

			</view>
			<view class="row">
				<view class="title flex justify-between">
					<view class="action">支付宝真实姓名：</view>
				</view>
				<view class="row-text flex justify-between align-center">
					<input type="text" value="" placeholder="请输入支付宝真实姓名" class="flex-sub" />
				</view>

			</view>
		</view>
		<view class="tab-item" v-if="waytype=='wechat'">
			<view class="row">
				<view class="title flex justify-between">
					<view class="action">微信号或其他账号：</view>
				</view>
				<view class="row-text flex justify-between align-center">
					<input type="text" value="" placeholder="请输入微信号或其他账号" class="flex-sub" />
				</view>
		
			</view>
			
		</view>
		<view class="tab-item" v-if="waytype=='bank'">
			<view class="row">
				<view class="title flex justify-between">
					<view class="action">银行卡账户：</view>
				</view>
				<view class="row-text flex justify-between align-center">
					<input type="text" value="" placeholder="请输入银行卡账户" class="flex-sub" />
				</view>
		
			</view>
			<view class="row">
				<view class="title flex justify-between">
					<view class="action">开户银行：</view>
				</view>
				<view class="row-text flex justify-between align-center">
					<input type="text" value="" placeholder="请输入开户银行" class="flex-sub" />
				</view>
		
			</view><view class="row">
				<view class="title flex justify-between">
					<view class="action">开户姓名：</view>
				</view>
				<view class="row-text flex justify-between align-center">
					<input type="text" value="" placeholder="请输入开户姓名" class="flex-sub" />
				</view>
		
			</view>
		</view>
		<view class="submitBtn">
			确认提现
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				waytype: 'alipay'
			};
		},
		methods: {
			RadioChange(e) {
				this.waytype = e.detail.value
			}
		}
	}
</script>

<style lang="scss">
	.group {
		padding-top: 40upx;

		.title {
			padding: 30upx 65upx;
			color: #a6a6a6;

			.action {
				color: #000;
				font-size: 30upx;
				font-weight: blod;
			}

			&.solid-bottom {
				border-bottom-color: #F0F0F0;
			}
		}

		.row {
			font-size: 26upx;
			padding: 0 30upx;

			.title {
				padding: 30upx 35upx;
			}

			.row-text {
				background: #f2f3f7;
				border-radius: 8upx;
				line-height: 70upx;
				padding: 0 30upx;
				height: 70upx;
			}

		}

		.checkgroup {
			font-size: 30upx;
			color: #000;
			font-weight: blod;

			radio {
				transform: scale(.7);
				margin-right: 16upx;
			}

			.radio-item+.radio-item {
				margin-left: 50upx;
			}
		}
		.submitBtn{
			margin: 50upx 30upx;
		}
	}
</style>
