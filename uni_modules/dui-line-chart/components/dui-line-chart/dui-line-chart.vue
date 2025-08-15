<template>
	<view class="canvas-box" :id="'canvas-' + canvasId">
		<canvas :style="{ width: canvasW + 'px', height: canvasH + 'px' }" :canvas-id="canvasId" :id="canvasId" @touchend="touchend" @touchstart="touchstart"></canvas>
	</view>
</template>

<script>
export default {
	emits: ['close', 'update:modelValue'],
	data() {
		return {
			type: 'line',
			canvasW: 0,
			canvasH: 0,
			canvasId: '',
			dpr: 1,
			toolTipsX: -1, //需要提示的x轴区域
			colorList: ['#1164ff', '#00f36d', '#b656ff', '#ff137d', '#000027']
		};
	},
	props: {
		// #ifdef VUE2
		value: Boolean,
		// #endif
		// #ifdef VUE3
		modelValue: Boolean,
		// #endif
		option: {
			type: Object,
			default: () => {
				return {};
			}
		}
	},
	created() {
		this.initCanvasId();
	},
	watch: {
		option: {
			handler(val) {
				const { xAxis, series } = val;
				if (xAxis && xAxis.data && series && series.length) {
					setTimeout(() => {
						this.updateCanvas();
						this.ctx.draw();
					}, 100);
				}
			},
			deep: true,
			immediate: true
		}
	},
	computed: {},
	methods: {
		
		getYAxisValue() {
					const PIECEBASIC = [1, 2, 5];
					const PIECELIST = [4, 5, 6];
					let valueArr = [0];
					
					this.option.series.forEach((ele) => {
						valueArr = valueArr.concat(ele.data);
					});
					
					const maxValue = Math.max(...valueArr);
					const magnitude = Math.pow(10, Math.floor(Math.log10(maxValue)));
					
					let everyPieceValue = magnitude;
					for (let base of PIECEBASIC) {
						if (base * magnitude >= maxValue / 4) {
							everyPieceValue = base * magnitude;
							break;
						}
					}
					
					const piece = Math.ceil(maxValue / everyPieceValue);
					const yAxisValue = Array.from({length: piece + 1}, (_, i) => i * everyPieceValue);
					
					return {
						yAxisValue,
						everyPieceValue
					};
				},
		setData() {
					const ctx = this.ctx;
					const { contentAreaH, contentAreaW, ltx, lty, lby } = this.contentArea;
					const { yAxisValue: yAxisData, everyPieceValue } = this.getYAxisValue();
					const yAxisLen = yAxisData.length;
					const xAxisDataLen = this.option.xAxis.data.length;
					const xAxisDataSize = parseInt(contentAreaW / xAxisDataLen);
					const aaa = contentAreaH / (yAxisLen - 1);
					const colorList = this.colorList;
					
					this.option.series.forEach((series, seriesInd) => {
						series.data.forEach((data, ind) => {
							const minxAxisData = 0; // 强制从0开始
							const circleRadius = this.toolTipsX == ind + 1 ? 4 : 3;
							const x = ltx + xAxisDataSize * ind + 0.5 * xAxisDataSize;
							const y = lby - (aaa / everyPieceValue) * (data - minxAxisData);
							
							// 绘制数据点
							ctx.beginPath();
							ctx.arc(x, y, circleRadius, 0, 2 * Math.PI);
							ctx.setFillStyle(colorList[seriesInd]);
							ctx.fill();
		 
							// 添加数值标签
							ctx.beginPath();
							ctx.setFontSize(10);
							ctx.setFillStyle('#666');
							ctx.setTextAlign('center');
							ctx.fillText(this.formatNumber(data), x, y - 12); // 在圆点上方12px显示数值
						});
					});
				},
		initCanvasId() {
			const _str = 'abcdefghijkmlnopqrstuvwxyzABCDEFGHIJKMLNOPQRSTUVWXYZ';
			const _len = _str.length;
			const _num = ~~(16 + Math.random() * 10);
			const _ind = () => ~~(Math.random() * _len);
			let result = '';
			for (let i = 0; i < _num; i++) {
				result += _str[_ind()];
			}
			this.canvasId = result + '-' + this.type;
		},

		initCanvas() {
			const systemInfo = uni.getSystemInfoSync();
			const pixel = systemInfo.pixelRatio;
			const paddingX = 30; //内边距x
			const paddingY = 40; //内边距y
			uni.createSelectorQuery()
				// #ifndef MP-ALIPAY
				.in(this)
				// #endif
				.select('#canvas-' + this.canvasId)
				.boundingClientRect((e) => {
					if (e.width > 0 && e.height > 0) {
						this.canvasW = e.width;
						this.canvasH = e.height;
						this.dpr = pixel;
					}
					this.ctx = uni.createCanvasContext(this.canvasId, this);
					this.contentArea = {
						ltx: paddingX,
						lty: paddingY,
						lbx: paddingX,
						lby: this.canvasH - paddingY,
						rtx: this.canvasW - paddingX,
						rty: paddingY,
						rbx: this.canvasW - paddingX,
						rby: this.canvasH - paddingY,
						contentAreaW: this.canvasW - paddingX * 2,
						contentAreaH: this.canvasH - paddingY * 2
					};
				})
				.exec();
		},

		initXAxis() {
			const ctx = this.ctx;
			const { contentAreaW, lbx, lby } = this.contentArea;
			const xAxisDataLen = this.option.xAxis.data.length;
			const xAxisDataSize = parseInt(contentAreaW / xAxisDataLen);
			let aa = lbx;
			ctx.beginPath();
			ctx.globalAlpha = 1;
			ctx.moveTo(lbx, lby + 3);
			ctx.lineTo(lbx, lby);
			ctx.setLineDash([], 0);
			ctx.setStrokeStyle('#939393');
			ctx.setLineWidth(1);
			ctx.stroke();
			this.option.xAxis.data.forEach((ele) => {
				ctx.beginPath();
				ctx.moveTo(aa, lby);
				ctx.setFontSize(12);
				ctx.setTextAlign('center');
				ctx.setTextBaseline('middle');
				ctx.setFillStyle('#888');
				ctx.fillText(ele, aa + (1 / 2) * xAxisDataSize, lby + 14);
				aa += xAxisDataSize;
				ctx.lineTo(aa, lby);
				ctx.lineTo(aa, lby + 3);
				ctx.stroke();
			});
		},

		initYAxis() {
			const ctx = this.ctx;
			const { contentAreaH, contentAreaW, ltx, lty, rtx } = this.contentArea;
			const { yAxisValue: yAxisData } = this.getYAxisValue();
			let fontSize = 12;
			const yAxisLen = yAxisData.length;
			const aaa = contentAreaH / (yAxisLen - 1);
			for (var i = 0; i < yAxisLen; i++) {
				let text = yAxisData[yAxisLen - 1 - i];
				let textAbs = Math.abs(text);
				if (textAbs >= 1000000) {
					text = text / 1000000 + 'M';
					fontSize = 10;
				} else if (textAbs >= 1000) {
					text = text / 1000 + 'k';
				}
				if (String(text).length >= 5) {
					fontSize = 9.0 - (String(text).length - 5) * 1;
				}
				ctx.beginPath();
				ctx.setStrokeStyle('#e1e7ee');
				ctx.setLineWidth(1);
				ctx.setLineDash([5, 10], 5);
				ctx.setFontSize(fontSize);
				ctx.setTextAlign('right');
				ctx.setTextBaseline('middle');
				ctx.setFillStyle('#888');
				ctx.fillText(text, ltx - 2, lty + i * aaa);
				ctx.setTextAlign('left');
				ctx.fillText(text, rtx + 2, lty + i * aaa);
				ctx.moveTo(ltx, lty + aaa * i);
				if (i != yAxisLen - 1) {
					ctx.lineTo(ltx + contentAreaW, lty + aaa * i);
				}
				ctx.stroke();
			}
		},

		setData() {
			const ctx = this.ctx;
			const { contentAreaH, contentAreaW, ltx, lty, lby } = this.contentArea;
			const { yAxisValue: yAxisData, everyPieceValue } = this.getYAxisValue();
			const yAxisLen = yAxisData.length;
			const xAxisDataLen = this.option.xAxis.data.length;
			const xAxisDataSize = parseInt(contentAreaW / xAxisDataLen);
			const aaa = contentAreaH / (yAxisLen - 1);
			const colorList = this.colorList;
			this.option.series.forEach((series, seriesInd) => {
				series.data.forEach((data, ind) => {
					const minxAxisData = yAxisData[0];
					const circleRadius = this.toolTipsX == ind + 1 ? 3 : 2;
					const x = ltx + xAxisDataSize * ind + 0.5 * xAxisDataSize;
					const y = lby - (aaa / everyPieceValue) * (data - minxAxisData);
					const lineWidth = series.lineStyle && series.lineStyle.width ? series.lineStyle.width : 2;
					const lineColor = series.lineStyle && series.lineStyle.color ? series.lineStyle.color : colorList[seriesInd];
					ctx.beginPath();
					ctx.arc(x, y, circleRadius, 0, 2 * Math.PI);
					ctx.moveTo(x, y);
					if (series.smooth) {
						//曲线画法待研究
					} else {
						ind != series.data.length - 1 &&
							ctx.lineTo(ltx + xAxisDataSize * (ind + 1) + 0.5 * xAxisDataSize, lby - (aaa / everyPieceValue) * (series.data[ind + 1] - minxAxisData));
					}
					ctx.setStrokeStyle(lineColor);
					ctx.setLineWidth(lineWidth);
					ctx.setLineDash([], 0);
					ctx.stroke();
					ctx.setFillStyle('#fff');
					ctx.fill();
				});
			});
		},

		setTitle() {
			const ctx = this.ctx;
			const { contentAreaH, contentAreaW, ltx, lty, lby, rtx } = this.contentArea;
			const { text, subText, textStyle = {}, subTextStyle = {} } = this.option.title;
			const fontSize = textStyle.fontSize || 14;
			const subFontSizeBase = 12;
			const subFontSize = subTextStyle.fontSize || subFontSizeBase;
			const color = textStyle.color || '#333';
			const subColor = subTextStyle.color || '#666';
			
			ctx.beginPath();
			ctx.setTextBaseline('top');
			let y = 4;
			if (text) {
				ctx.setFillStyle(color);
				ctx.setFontSize(fontSize);
				ctx.setTextAlign('left');
				if (textStyle.textAlign) {
					let x = ltx;
					switch (textStyle.textAlign) {
						case 'right':
							x = rtx;
							break;
						case 'center':
							x = ltx + contentAreaW / 2;
							break;
						default:
							break;
					}
					ctx.setTextAlign(textStyle.textAlign);
					ctx.fillText(text, x, y);
				} else {
					ctx.fillText(text, ltx, y);
				}
			}

			if (subText) {
				ctx.setFontSize(subFontSize);
				ctx.setFillStyle(subColor);
				ctx.setTextAlign('left');
				let subY = text ? fontSize * 1.2 + y : Math.abs(20 - subFontSize + subFontSizeBase);
				if (subTextStyle.textAlign) {
					let subX = ltx;
					switch (subTextStyle.textAlign) {
						case 'right':
							subX = rtx;
							break;
						case 'center':
							subX = ltx + contentAreaW / 2;
							break;
						default:
							break;
					}
					ctx.setTextAlign(subTextStyle.textAlign);
					ctx.fillText(subText, subX, subY);
				} else {
					ctx.fillText(subText, ltx, subY);
				}
			}
		},

		seriesName() {
			const colorList = this.colorList;
			const ctx = this.ctx;
			const seriesLen = this.option.series.length;
			const { contentAreaH, contentAreaW, ltx, lty, lbx, lby, rtx } = this.contentArea;
			let seriesNameTotalW = 0;
			const lineW = 18;
			const lineNameGap = 3;
			const seriesNameWList = [];
			this.option.series.forEach((ele, ind) => {
				const nameW = ctx.measureText(ele.name).width;
				let gapW = 0;
				if (ind != 0) {
					gapW = 6;
				}
				const seriesNameW = lineW + lineNameGap + nameW + gapW;
				seriesNameWList.push(seriesNameW);
				seriesNameTotalW += seriesNameW;
			});
			//居中起始点x坐标
			let startX = (contentAreaW - seriesNameTotalW) / 2 + lbx;
			//居中起始点y坐标
			const startY = lby + 32;
			this.option.series.forEach((ele, ind) => {
				ctx.setTextBaseline('middle');
				ctx.beginPath();
				ctx.setLineWidth(2);
				ctx.moveTo(startX, startY);
				ctx.lineTo(startX + lineW, startY);
				ctx.setStrokeStyle(colorList[ind]);
				ctx.stroke();

				ctx.arc(startX + lineW / 2, startY, 2, 0, 2 * Math.PI);
				ctx.setFillStyle('#fff');
				ctx.stroke();
				ctx.fill();

				ctx.beginPath();
				ctx.setTextAlign('left');
				ctx.setFontSize(10);
				ctx.setFillStyle(colorList[ind]);
				ctx.setFillStyle('#555');
				ctx.fillText(ele.name, startX + lineW + lineNameGap, startY);
				ctx.stroke();

				startX += seriesNameWList[ind] + (ind == 0 ? 6 : 0);
			});
		},

		initAxis() {
			const showXAxis = this.option.xAxis && this.option.xAxis.hasOwnProperty('show') ? this.option.xAxis.show : true;
			const showYAxis = this.option.yAxis && this.option.yAxis.hasOwnProperty('show') ? this.option.yAxis.show : true;
			showXAxis && this.initXAxis();
			showYAxis && this.initYAxis();
		},

		/**
		 * @param {x}  提示区域x轴区域
		 */
		showToolTips(x) {
			const ctx = this.ctx;
			const { contentAreaH, contentAreaW, lty, ltx } = this.contentArea;
			const xAxisDataLen = this.option.xAxis.data.length;
			const xAxisDataSize = parseInt(contentAreaW / xAxisDataLen);
			const colorList = this.colorList;
			this.toolTipsX = x;
			this.updateCanvas();

			ctx.beginPath();
			ctx.setFillStyle('#ddd');
			ctx.globalAlpha = 0.3;
			ctx.fillRect((x - 1) * xAxisDataSize + ltx, lty, xAxisDataSize, contentAreaH);

			// 提示白框部分-----------
			ctx.setFillStyle('#fff');
			ctx.globalAlpha = 1;
			ctx.setShadow(5, 5, 30, '#ddd');
			let rectBoxW = 0; //提示白框宽度
			let rectBoxH = 0; //提示白框高度
			let rectX = x * xAxisDataSize + ltx; //提示白框横坐标
			const PAD = 10; //提示白框内边框大小
			const smallRectSize = 9; //小圆形大小
			const NameGap = 5;
			const verticalGap = 8;
			let seriesNVMaxSize = 0;
			let seriesNMaxSize = 0;
			rectBoxW += 2 * PAD + smallRectSize + 2 * NameGap;
			rectBoxH += 2 * PAD;
			this.option.series.forEach((ele, ind) => {
				const nvW = ctx.measureText(ele.name).width + ctx.measureText(ele.data[x - 1]).width;
				const nW = ctx.measureText(ele.name).width;
				if (nvW > seriesNVMaxSize) {
					seriesNVMaxSize = nvW;
				}
				if (nW > seriesNMaxSize) {
					seriesNMaxSize = nW;
				}
				rectBoxH += smallRectSize + (ind == 0 ? 0 : verticalGap);
			});
			rectBoxW += seriesNVMaxSize;
			let whileJudge = rectX + rectBoxW > this.canvasW;
			if (whileJudge) {
				rectX = (x - 1) * xAxisDataSize + ltx - rectBoxW;
			}
			ctx.fillRect(rectX, contentAreaH / 2, rectBoxW, rectBoxH);
			// --------------提示白框部分

			//提示框内容部分--------------
			let seriesY = contentAreaH / 2 + PAD;
			this.option.series.forEach((ele, ind) => {
				const nW = ctx.measureText(ele.name).width;
				const value = ele.data[x - 1];
				let seriesXBase = x * xAxisDataSize + ltx;
				seriesY += ind == 0 ? 0 : smallRectSize + verticalGap;
				if (whileJudge) {
					seriesXBase = (x - 1) * xAxisDataSize + ltx - rectBoxW;
				}
				ctx.setFillStyle(colorList[ind]);
				ctx.setTextBaseline('top');
				ctx.setTextAlign('left');
				ctx.fillRect(seriesXBase + PAD, seriesY, smallRectSize, smallRectSize);
				ctx.setFillStyle('#666');
				ctx.fillText(ele.name, seriesXBase + PAD + smallRectSize + NameGap, seriesY);
				ctx.setFillStyle('#000');
				ctx.fillText(value, seriesXBase + PAD + smallRectSize + 2 * NameGap + seriesNMaxSize, seriesY);
			});
			//----------------提示框内容部分
			this.ctx.draw();

			clearTimeout(this.toolTipsTimeout);
			this.toolTipsTimeout = setTimeout(() => {
				this.toolTipsX = -1;
				this.ctx.clearRect(0, 0, this.canvasW, this.canvasH);
				this.updateCanvas();
				this.ctx.draw();
			}, 2500);
		},

		touchstart(e) {
			const { contentAreaW, lbx, lby } = this.contentArea;
			const xAxisDataLen = this.option.xAxis.data.length;
			const xAxisDataSize = parseInt(contentAreaW / xAxisDataLen);
			const { x, y } = e.touches[0];
			if (!this.option.tooltip.show) {
				return;
			}
			for (let i = 1; i <= xAxisDataLen; i++) {
				if (x - lbx <= i * xAxisDataSize) {
					this.showToolTips(i);
					return;
				}
			}
		},

		touchend(e) {
			// console.log(e)
			// console.log(e.detail.x)
		},

		updateCanvas() {
			this.initAxis();
			this.setData();
			this.setTitle();
			this.seriesName();
		},

		preciseMultiply(num1, num2) {
			let m = 0;
			const s1 = num1.toString();
			const s2 = num2.toString();
			try {
				m += s1.split('.')[1].length;
			} catch (e) {}
			try {
				m += s2.split('.')[1].length;
			} catch (e) {}
			return (Number(s1.replace('.', '')) * Number(s2.replace('.', ''))) / Math.pow(10, m);
		}
	},
	mounted() {
		this.initCanvas();
		// setTimeout(() => {
		// 	this.updateCanvas();
		// 	this.ctx.draw();
		// }, 100);
	}
};
</script>

<style lang="scss" scoped>
$activeColor: #2e78f0;
.canvas-box {
	width: 100%;
	height: 100%;
}
</style>
