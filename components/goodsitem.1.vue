<template>
	<view class="goodsbox">
		<div class="goods flex">
			<div class="imgbox">
				<image src="/static/demo/1.png" mode="widthFix"></image>
			</div>
			<div class="flex-sub">
				<div class="name">戴安娜玫瑰花</div>
				<div>
					<span>20支/扎</span>
					<span class="ml40">粉色</span>
				</div>
				<div class="price">
					<span class="red">￥</span>
					<span class="red ft38">19.8</span>
					<span>起</span>
				</div>
				<div class="btn flex align-center justify-center" :class="{'active':isOpen}" @click="tapOpen">
					{{isOpen?'收起':'采购'}}
				</div>
			</div>
		</div>
		<template v-if="isOpen">
			<div class="maillist" :class="{active:isOpenitem}">
				<div class="mail-item ">
					<div class="flex">
						<div class="imgbox">
							<image src="/static/demo/demo.png" mode="widthFix"></image>
						</div>
						<div class="info flex-sub">
							<div class="name">
								完美鲜花批发
							</div>
							<div><span>库存:489</span><span class="ml25">销量:54</span></div>
							<div class="flex justify-between align-center mt20">
								<span class="price">
									<em>￥19.8</em>/扎
								</span>
								<span class="btn" @tap="buygoods">采购</span>
							</div>
						</div>
					</div>
					<div class="flex align-center mt20">
						<div class="tag tag1"></div>
						<div class="state">关注的店</div>
						<div class="mailname" @click="tapMailName">完美鲜花批发></div>
					</div>
					<div class="goodstag grid col-3 mt20">
						<view>等级:B级</view>
						<view>枝长:80CM</view>
						<view>产地:云南昆明</view>
						<view>优点:花头漂亮</view>
						<view>瑕疵:刺多</view>
						<view>成熟度:中熟</view>
					</div>
				</div>
			</div>
		</template>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				isOpen: false,
				isOpenitem: false
			};
		},
		methods: {
			tapMailName() {
				this.$emit('showMail')
			},
			tapOpen() {
				if (this.isOpen) {
					this.isOpenitem = false;
					this.$nextTick(() => {
						this.isOpen = false;
					})
				} else {
					this.isOpen = true;
					this.$nextTick(() => {
						this.isOpenitem = true
					})
				}

			},
			buygoods(){
				this.$emit('buygoods')
			}
		}
	}
</script>

<style lang="scss" scoped>
	.ml40 {
		margin-left: 40upx;
	}

	.ml25 {
		margin-left: 25upx;
	}

	.mt20 {
		margin-top: 20upx;
	}

	.mt30 {
		margin-top: 30upx;
	}

	.goodsbox {
		padding: 0 30upx 15upx 22upx;
		box-shadow: 0 4upx 16upx 0 rgba(213, 213, 213, 1);
		overflow: hidden;
		background: #fff;

		&+.goodsbox {
			margin-top: 20upx;
		}

		.goods {
			font-size: 24upx;
			color: #9F9F9F;
			position: relative;
			padding: 14upx;
			border-radius: 8upx;
			z-index: 99;
			background: #fff;
			padding-top: 15upx;

			.imgbox {
				width: 196upx;
				height: 196upx;
				overflow: hidden;
				margin-right: 20upx;
				border-radius: 10upx;

				image {
					display: block;
					width: 100%;
					height: 100%;
				}
			}

			.name {
				color: #2E2E2E;
				font-size: 28upx;
				margin-bottom: 20upx;
				overflow: hidden;
				text-overflow: ellipsis;
				white-space: nowrap;
			}

			.btn {
				border: 1px solid #FF5454;
				border-radius: 8upx;
				line-height: 48upx;
				width: 120upx;
				text-align: center;
				position: absolute;
				right: 18upx;
				bottom: 20upx;
				color: #FF5454;

				&:after {
					content: '';
					height: 8upx;
					width: 12upx;
					margin-left: 10upx;
					display: block;
					background: url(../static/shopping_arrow@2x.png) no-repeat center center;
					background-size: 100% auto;
					transition: all .3s;
				}

				&.active:after {
					transform: rotate(180deg);
				}
			}

			.price {
				margin-top: 60upx;
				font-size: 22upx;
				color: #DADADA;

				.red {
					color: #FD3C3E;
				}

				.ft38 {
					font-size: 38upx;
					margin-right: 8upx;
				}
			}
		}

		.maillist {
			z-index: 0;
			background: #EAEAEA;
			transition: all .3s;
			transform: translateY(-50%);
			height: 0px;
			overflow: hidden;

			&.active {
				transform: translateY(0px);
				height: auto;
				transition: all .3s;
			}

			.mail-item {
				background: #F5F5F5;

				padding: 22upx 15upx;
				font-size: 24upx;
				color: #9F9F9F;
				position: relative;

				&+.mail-item {
					margin-top: 10upx;
				}

				&:before {
					display: block;
					content: '';
					height: 24upx;
					position: absolute;
					left: 0;
					right: 0;
					top: -5upx;
					background: url(/static/arrowbg.png) no-repeat center center;
					background-size: 100% auto;
				}

				.imgbox {
					width: 140upx;
					background: #fff;
					border: 1px solid #E8E8E8;
					border-radius: 10upx;
					margin-right: 16upx;

					image {
						width: 100%;
					}
				}

				.name {
					font-size: 26upx;
					color: #FF9518;
					margin-bottom: 18upx;
				}

				.price {
					font-size: 22upx;
					color: #C1C1C1;

					em {
						font-style: normal;
						display: inline-block;
						color: #FD3C3E;
						font-size: 28upx;
					}
				}

				.btn {
					background: #FF9518;
					font-size: 24upx;
					color: #fff;
					border-radius: 8upx;
					width: 110upx;
					height: 48upx;
					display: block;
					text-align: center;
					line-height: 48upx;
				}

				.state {
					color: #FF9518;
					font-size: 22upx;
					margin-left: 10upx;

				}

				.tag {
					width: 66upx;
					height: 23upx;
					background: no-repeat center center;
					background-size: 100% auto;
				}

				.tag1 {
					background-image: url(/static/proprietary_label@2x.png);
				}

				.tag2 {
					background-image: url(/static/brand_label@2x.png);
				}

				.tag3 {
					background-image: url(/static/base_tag@2x.png);
				}

				.tag4 {
					width: 22upx;
					height: 21upx;
					background-image: url(/static/base_tag@2x.png);
				}

				.mailname {
					color: #7E7E7E;
					font-size: 22upx;
					margin-left: 10upx;
				}

				.goodstag {
					background: #fff;
					padding: 25upx 10upx;
					border-radius: 8upx;
					color: #515151;
					font-size: 20upx;

					view {
						padding: 5upx 0;
					}
				}
			}
		}
	}
</style>
