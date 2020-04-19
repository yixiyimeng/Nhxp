<template>
	<view class="cate-item">
		<div class="title">
			玫瑰类——戴安娜
		</div>
		<div class="flex infobox">
			<div class="imgbox">
				<image src="../../static/demo/1.png" mode="widthFix"></image>
			</div>
			<div class="flex-sub">
				<div class="flex justify-between align-center padding-bottom-xs">
					<div class="name">戴安娜玫瑰花</div>
					<div>
						<span class="state" :class="{'text-yellow':switchA}">{{switchA?'上线':'下线'}}</span>
						<switch class="yellow" @change="SwitchA" :class="switchA?'checked':''" :checked="switchA?true:false"></switch>
					</div>
				</div>
				<div class="flex info flex-wrap">
					<view>等级：A</view>
					<view>单位：10支/扎</view>
					<view>长度：80cm</view>
					<view>颜色：红色</view>
					<view>销量：98</view>
					<view>库存：168</view>
				</div>
			</div>
		</div>
		<div class="btnbar flex align-center">
			<div class="flex-sub"><span>单价：</span>
				<span class='price'>￥</span>
				<span class='price'>19.8</span>
				<navigator url="/shop/apply/apply">申请特价促销></navigator>
			</div>
			<button class="btn">删除</button>
			<button class="btn">编辑</button>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				switchA: false
			};
		},
		methods: {
			SwitchA(e) {
				this.switchA = e.detail.value
			},
		}
	}
</script>

<style lang="scss">
	.cate-item {
		background: #fff;
		padding: 0 14upx;
		box-shadow: 0 4upx 16upx 0 rgba(213, 213, 213, 1);
		border-radius: 8upx;
		color: #666;
		font-size: 24upx;

		.title {
			color: #A0A0A0;
			font-size: 28upx;
			padding: 20upx 0;
		}

		.infobox {
			padding-bottom: 22upx;
			border-bottom: 1px solid #EDEDED;

			.info {
				view {
					width: 30%;
					margin: 10upx 0;

					&:nth-child(3n+2) {
						width: 40%;
					}
				}
			}
		}

		.imgbox {
			width: 160upx;
			height: 160upx;
			border-radius: 8upx;
			overflow: hidden;
			margin-right: 18upx;

			image {
				width: 100%;
			}
		}

		.btnbar {
			font-size: 24upx;
			padding: 18upx 0;
			color: #666;

			.price {
				color: #FD3C3E;
				font-size: 22upx;

				&+.price {
					font-size: 36upx;
				}
			}

			navigator {
				display: inline-block;
				color: #19A967;
				font-size: 26upx;
				margin-left: 10upx;
			}
		}

		.btnbar .btn {
			font-size: 26upx;
			width: 134upx;
			height: 59upx;
			text-align: center;
			line-height: 59upx;
			border-radius: 8upx;
			color: #FD3C3E;
			background: #fff;
			border: 1px solid #FD3C3E;

			&+.btn {
				background: #19A967;
				color: #fff;
				margin-left: 22upx;
				border-color: #19A967;
			}
		}

		.name {
			color: #2E2E2E;
			font-size: 32upx;
		}
		.state{
			font-size: 26upx;
			margin-right: 25upx;
			line-height: 32upx;
			vertical-align: middle;
		}
	}
</style>
