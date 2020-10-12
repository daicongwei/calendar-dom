<template>
	<div class="hello">
		<h1>原始样式</h1>
		<Calendar></Calendar>

		<h1>自定义样式（2020年10月份有标记）</h1>
		<div class="calendarBox">
			<Calendar
				@choseDay="clickDay"
				ref="Calendar"
				:markDateMore="arr"
			></Calendar>
			<button class="todatBtn" @click="toToday">查看今天</button>
		</div>
	</div>
</template>

<script>
import Calendar from "vue-calendar-component";
export default {
	name: "HelloWorld",
	components: {
		Calendar,
	},
	data() {
		return {
			arr: [
				{ date: "2020/10/19", className: "mark_bule" },
				{ date: "2020/10/20", className: "mark_bule" },
				{ date: "2020/10/21", className: "mark_bule" },
				{ date: "2020/10/23", className: "mark_yellow" },
				{ date: "2020/10/25", className: "mark_yellow" },
				{ date: "2020/10/26", className: "mark_yellow" },
			],
		};
	},
	methods: {
		//调用方法实现转到上个月
		toPreYue() {
			this.$refs.Calendar.PreMonth();
		},
		//调用方法实现转到下个月
		toNexYue() {
			this.$refs.Calendar.NextMonth();
		},
		// 回到今天
		toToday() {
			this.$refs.Calendar.ChoseMonth("2020-9-20");
		},
		// 选中的某天
		clickDay(data) {
			console.log(data, "选中某天"); //选中某天
		},
	},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h1 {
	text-align: center;
}
.calendarBox {
	width: 400px;
	border: red solid 1px;
	margin: 0 auto;
	// height: 412px;
	position: relative;
	.todatBtn {
		position: absolute;
		height: 24px;
		top: 35px;
		right: 60px;
		z-index: 1;
		width: 68px;
		height: 24px;
		background: #e8e8e8;
		border-radius: 12px;
		border: 1px solid #d6d6d6;
		text-align: center;
		line-height: 22px;
		font-size: 11px;
		font-weight: 600;
		color: #666666;
		cursor: pointer;
		user-select: none;
		outline: none;
		&:hover {
			background: #e1e1e1;
		}
		&:active {
			background: #e8e8e8;
		}
	}
	/deep/.wh_content_all {
		background-color: #fff;
	}
	/deep/.wh_top_changge {
		padding: 30px;
		padding-bottom: 20px;
		display: block;
		position: relative;
		& > li {
			.wh_jiantou1,
			.wh_jiantou2 {
				display: none;
			}
			&:first-of-type {
				width: 24px;
				height: 24px;
				position: absolute;
				top: 35px;
				right: 134px;
				background: url("../assets/calendar_bgL.png");
				background-size: 24px 24px;
			}
			&:last-of-type {
				width: 24px;
				height: 24px;
				position: absolute;
				top: 35px;
				right: 30px;
				background: url("../assets/calendar_bgR.png");
				background-size: 24px 24px;
			}
		}
		.wh_content_li {
			display: block;
			font-size: 24px;
			font-weight: 600;
			color: #000000;
			height: auto;
		}
	}
	/deep/.wh_content {
		padding: 0 20px;
		box-sizing: border-box;
		justify-content: flex-start;
		.wh_content_item {
			width: calc(~"100% / 7");
			height: 44px;
			line-height: 44px;
			border-radius: 50%;

			.wh_top_tag {
				font-weight: 600;
				color: #333333;
				font-size: 15px;
			}
			.wh_item_date {
				font-size: 14px;
				font-weight: 500;
				color: #777777;
				border-radius: 50%;
				&:hover {
					background: #4e9ef8;
					color: #fff;
				}
			}
			.wh_other_dayhide {
				color: #e1e4e7;
			}
			.wh_isToday {
				background: #3c96fb;
				color: #fff;
			}
			.wh_chose_day {
				.wh_isToday;
			}
			.mark_bule {
				position: relative;
				&::after {
					content: "";
					display: inline-block;
					width: 6px;
					height: 6px;
					border-radius: 6px;
					background: #3c96fb;
					position: absolute;
					bottom: 0;
					left: 50%;
					margin-left: -3px;
				}
			}
			.mark_yellow {
				position: relative;
				&::after {
					content: "";
					display: inline-block;
					width: 6px;
					height: 6px;
					border-radius: 6px;
					background: #f7b500;
					position: absolute;
					bottom: 0;
					left: 50%;
					margin-left: -3px;
				}
			}
		}
	}
}
</style>
