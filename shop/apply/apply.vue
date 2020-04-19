<template>
	<view>
		<div class="tip flex align-center">
			<text class="cuIcon cuIcon-creative"></text>
			<text>请认真填写企业(个人)资料，以便于我们了解您的情况，认真所需的个人信息不会公开给任何组合和个人。
			</text>
		</div>
		<form>
			<view class="cu-form-group">
				<view class="title">公司名称：</view>
				<input placeholder-style="color:#C4C4C4" placeholder="请填写个人或公司名称" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">店铺名称：</view>
				<input placeholder-style="color:#C4C4C4" placeholder="例如：方德玫瑰" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">负责人：</view>
				<input placeholder-style="color:#C4C4C4" placeholder="请填写负责人姓名" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">联系电话：</view>
				<input type="number" placeholder-style="color:#C4C4C4" placeholder="请输入联系方式" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">紧急联络人：</view>
				<input type="number" placeholder-style="color:#C4C4C4" placeholder="请填写紧急联系人" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">地址：</view>
				<input placeholder-style="color:#C4C4C4" placeholder="请填写详细地址" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">供应品种：</view>
				<input placeholder-style="color:#C4C4C4" placeholder="请输入供应的品种，便平台审核" name="input"></input>
			</view>
			<view class="cu-form-group">
				<view class="title">负责人身份证</view>
				<input type="idcard" placeholder-style="color:#C4C4C4" placeholder="请输入身份证号" name="input"></input>
			</view>
			<div class="cu-form-group uploadCard flex justify-between">
				<div class="upload" @tap="upload">
					<image src="/static/shop/positive@2x.png" mode="widthFix"></image>
				</div>
				<div class="upload">
					<image src="/static/shop/reverse@2x.png" mode="widthFix"></image>
				</div>
			</div>
			<div class="sendBtn">
				确认提交
			</div>
			<div class="txt">
				我已经阅读，并同意
				<navigator url="">
					《供货商服务协议》
				</navigator>
			</div>
		</form>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			};
		},
		methods:{
			upload() {
				uni.chooseImage({
					count: 1, //默认9
					sizeType: ['original', 'compressed'], //可以指定是原图还是压缩图，默认二者都有
					sourceType: ['album','camera'], //从相册选择
					success: function(res) {
						console.log(JSON.stringify(res.tempFilePaths));
					}
				});
			}
		}
	}
</script>

<style lang="scss">
	page {
		height: 100%;
		background: #fff;
	}

	.tip {
		padding: 20upx 30upx;
		color: #545454;
		font-size: 26upx;
		line-height: 38upx;
		background: #F7F7F7;

		.cuIcon {
			color: #19A967;
			font-size: 48upx;
			margin-right: 10upx;
		}
	}

	.cu-form-group input {
		text-align: right;
	}

	.uploadCard {
		background: #fff;
		padding: 38upx 30upx;
	}

	.uploadCard .upload {
		width: 324upx;
		height: 279upx;
	}

	.sendBtn {
		width: 690upx;
		height: 100upx;
		background: #19A967;
		box-shadow: 0 9upx 27upx 0 rgba(25, 169, 103, 0.58);
		border-radius: 12upx;
		color: #fff;
		text-align: center;
		font-size: 30upx;
		line-height: 100upx;
		margin: 30upx auto
	}

	.txt {
		padding: 10upx 0 40upx;
		font-size: 26upx;
		text-align: center;
		color: #6F6F6F;

		navigator {
			color: #19A967;
			display: inline;
		}
	}
</style>
