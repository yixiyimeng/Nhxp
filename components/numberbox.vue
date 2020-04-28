<template>
	<view class="operatebar flex align-center">
		<div class="minusBtn" @tap="reduce">
			<image src="/static/cut_back@2x.png" mode="widthFix"></image>
		</div>
		<input type="number" v-model="inputValue" :disabled="disabled" @blur="blur" class="num" @change="changenum" />
		<div class="addBtn"@tap="plus">
			<image src="/static/increase@2x.png" mode="widthFix"></image>
		</div>
	</view>
</template>

<script>
	export default {
		name: "Numberbox",
		props: {
			value: {
				type: Number,
				default: 1
			},
			//最小值
			min: {
				type: Number,
				default: 1
			},
			//最大值
			max: {
				type: Number,
				default: 99
			},
			//迈步大小 1 1.1 10...
			step: {
				type: Number,
				default: 1
			},
			//是否禁用操作
			disabled: {
				type: Boolean,
				default: false
			},
			//加减图标大小 rpx
			iconSize: {
				type: Number,
				default: 26
			},
			iconColor: {
				type: String,
				default: "#666666"
			},
			//input 高度
			height: {
				type: Number,
				default: 42
			},
			//input 宽度
			width: {
				type: Number,
				default: 80
			},
			size: {
				type: Number,
				default: 28
			},
			//input 背景颜色
			bgcolor: {
				type: String,
				default: "#F5F5F5"
			},
			//input 字体颜色
			color: {
				type: String,
				default: "#333"
			},
			//索引值，列表中使用
			index: {
				type: [Number, String],
				default: 0
			},
			//自定义参数
			custom: {
				type: [Number, String],
				default: 0
			}
		},
		created() {
			this.inputValue = +this.value
		},
		data() {
			return {
				inputValue: 0
			};
		},
		watch: {
			value(val) {
				this.inputValue = +val
			}
		},
		methods: {
			getScale() {
				let scale = 1;
				//浮点型
				if (!Number.isInteger(this.step)) {
					scale = Math.pow(10, (this.step + '').split('.')[1].length)
				}
				return scale;
			},
			calcNum: function(type) {
				if (this.disabled) {
					return
				}
				const scale = this.getScale()
				let num = this.value * scale
				let step = this.step * scale
				if (type === 'reduce') {
					num -= step
				} else if (type === 'plus') {
					num += step
				}
				let value = num / scale
				if (type === "plus" && value < this.min) {
					value = this.min
				} else if (type === "reduce" && value > this.max) {
					value = this.max
				}
				if (value < this.min || value > this.max) {
					return
				}
				this.handleChange(value, type)
			},
			plus: function() {
				this.calcNum("plus")
			},
			reduce: function() {
				this.calcNum("reduce")
			},
			blur: function(e) {
				let value = e.detail.value
				if (value) {
					/* Number.isInteger 判断是否是整数 */
					if (~value.indexOf(".") && Number.isInteger(this.step)) {
						value = value.split(".")[0]
					}
					value = Number(value)
					if (value > this.max) {
						value = this.max
					} else if (value < this.min) {
						value = this.min
					}
				} else {
					value = this.min
				}
				if (value == this.value && value != this.inputValue) {
					this.inputValue = value
				}
				this.handleChange(value, "blur")
			},
			handleChange(value, type) {
				if (this.disabled) return;
				this.$emit('change', {
					value: value,
					type: type,
					index: this.index,
					custom: this.custom
				})
			}
		}
	}
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
</style>
