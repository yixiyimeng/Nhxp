<template>
	<view class="operatebar flex align-center">
		<div class="minusBtn" @click.stop="minus" v-if="count>0||isShowMinus">
			<image src="/static/cut_back@2x.png" mode="widthFix"></image>
		</div>
		<input type="number" v-if="count>0||isShowMinus" class="num" :value="count" @change="changenum" />
		<div class="addBtn" @click.stop="add">
			<image src="/static/increase@2x.png" mode="widthFix"></image>
		</div>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				num: 0
			};
		},
		// model: {
		// 	value: this.count,
		// 	callback: newVisible => this.count = newVisible
		// },
		props: {
			// num:{
			// 	type: Number,
			// 	default: 0
			// },
			count: {
				type: Number,
				default: 0
			},
			goodsId: {
				type: [String, Number],
				default: ''
			},
			stock: {
				type: Number,
				default: 1000
			},
			isShowMinus: {
				type: Boolean,
				default: true
			},
			color: {
				type: [String, Number],
				default: 1
			}
		},
		watch: {
			count(newValue, oldValue) {
				console.log(newValue)
				if (newValue != oldValue) {

					//this.num = newValue;
				}
			},
			// num(newValue, oldValue) {
			// 	if (newValue != oldValue) {
			// 		this.$emit('changeCount', { num: this.num, id: this.goodsId });
			// 	}
			// }
		},
		created() {
			this.num = this.count;
		},
		methods: {
			minus() {
				this.num = this.count
				if (this.count > 0) {
					this.num--;
				} else {
					this.num = 0;
				}
				this.$emit('changeCount', {
					num: this.num,
					id: this.goodsId
				});
			},
			add() {
				this.num = this.count 
				if (this.stock > this.num) {
					this.num++;
				} else {
					uni.showToast({
						title: '超出库存了',
						icon: 'none'
					});
				}
				this.$emit('changeCount', {
					num: this.num,
					id: this.goodsId
				});
			},
			changenum(e) {
				console.log('chufa'+JSON.stringify(e.detail.value))
				this.num = parseInt(e.detail.value)
				if (!this.num || this.num <= 0) {
					this.num = 1;
				} else if (this.stock < this.num) {
					uni.showToast({
						title: '超出库存了',
						icon: 'none'
					});
					this.num = this.stock;
				}
				this.$emit('changeCount', {
					num: this.num,
					id: this.goodsId
				});
			}
		}
	};
</script>

<style scoped>
	.operatebar image {
		height: 56upx;
		width: 56upx;
		display: block;
	}

	.operatebar div {
		display: inline-block;
		vertical-align: middle;
	}

	.operatebar .num {
		width: 60upx;
		text-align: center;
		font-size: 32upx;
		display: inline-block;
		color: #010101;
		vertical-align: middle;
		color: #fc733b;
	}

	/* .num {
	width: 60upx;
	color: #58585a;
	font-size: 22upx;
}
.minusBtn,
.addBtn {
	height: 52upx;
	width: 52upx;
	display: inline-block;
}
.minusBtn image,
.addBtn image {
	display: block;
	width: 100%;
	height: 100%;
} */
</style>
