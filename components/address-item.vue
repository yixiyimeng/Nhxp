<template>
	<view class="card bg-white">
		<view class="flex align-center card-bt">
			<image src="/static/icon15.png" mode="widthFix" class="addr"></image>
			<view class="flex-sub">
				<view class="">
					<text class="name">王小姐</text>
					<text>13888145285</text>
				</view>
				<view class="margin-top-sm">云南省昆明市五华区1111号</view>
			</view>
			<image src="/static/icon18.png" mode="widthFix" class="arrow"></image>
		</view>
		<view class="card-ft flex align-center justify-between">
			<label>
				<checkbox class="round orange" /><text>设为默认</text>
			</label>
			<view class="flex">
				<view class="edit">
					<image src="/static/icon16.png" mode="widthFix"></image>
					<text>编辑</text>
				</view>
				<view class="del">
					<image src="/static/icon17.png" mode="widthFix"></image>
					<text>删除</text>
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
	.card {
		border-radius: 20upx;
		font-size: 26upx;
		margin: 0 26upx 30upx;
		color: #000;

		.card-bt {
			padding: 30upx 36upx;
		}

		.name {
			font-size: 28upx;
			font-weight: bold;
			margin-right: 28upx;
		}

		.addr {
			width: 26upx;
			margin-right: 60upx;
		}

		.arrow {
			width: 17upx;
		}

		.card-ft {
			border-top: 1px solid #e5e5e5;
			padding: 0 36upx;
			height: 65upx;

			.round {
				transform: scale(.7);
			}

			image,
			text {
				display: inline-block;
				vertical-align: middle;
			}

			.edit {
				image {
					width: 34upx;
					margin-right: 20upx;
				}
			}

			.del {
				margin-left: 26upx;

				image {
					width: 37upx;
					margin-right: 20upx;
				}
			}
		}
	}
</style>
