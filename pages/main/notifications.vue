<template>
	<view class="m-page m-main-bg" style="padding-bottom: 100rpx;">
		<cu-custom :isBack="true" bgColor="bg-shadeTop text-white">
			<!-- <block slot="backText"></block> -->
			<block slot="content">通知</block>
			<block slot="right">
				<view class="cuIcon cuIcon-noticefill m-settings"></view>
			</block>
		</cu-custom>
		<view class="m-content_">
			<scroll-view scroll-x class="nav">
				<view class="flex text-center">
					<view class="cu-item flex-sub m-tab" :class="index==TabCur?'m-tab-selected cur':''" v-for="(item,index) in tabs"
					 :key="index" @tap="tabSelect" :data-id="index">
						{{item}}
					</view>
				</view>
			</scroll-view>
			<view class="m-notifications-list" v-show="TabCur==1">
				<view class="" v-for="index in 10" :key="index">
					<view class="m-notifications-item">

						<view class="m-notification-left">

							<view class="cu-avatar lg round margin-left" style="background-image:url('../../static/images/user.jpg');"></view>
							<view class="m-detail">
								<view class="m-notif-title">注塑之家</view>
								<view class="m-notif-detail m-text-gray">发布了新视频 · 11-23</view>
							</view>
						</view>
						<view class="m-notification-right">
							<view class="m-thumb-wrapper">
								<image src="../../static/images/bg-music.jpeg" mode=""></image>
								<text class="cuIcon cuIcon-playfill"></text>
							</view>
						</view>

					</view>
					<view class="" style="height: 1px; background-color: #21213C; margin-left: 150rpx;">

					</view>

				</view>

			</view>
			<view class="margin-top" v-show="TabCur==0">
				<view class="cu-list menu-avatar">
					<view class="cu-item radius" :class="modalName=='move-box-'+ index?'move-cur':''" v-for="(item,index) in chats" :key="index"
					 @touchstart="ListTouchStart" @touchmove="ListTouchMove" @touchend="ListTouchEnd" :data-target="'move-box-' + index"
					 @click="toChat(index)">
						<view class="cu-avatar round lg" :style="[{backgroundImage:'url(../../static/images/user.jpg)'}]"></view>
						<view class="content">
							<view class="text-white">{{item.name}}</view>
							<view class="text-grey text-xs">{{item.date}}</view>
							<view class="text-gray text-sm">{{item.desc}}</view>
						</view>
						<view class="move">
							<view class="bg-grey">置顶</view>
							<view class="bg-red">删除</view>
						</view>
					</view>
				</view>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				TabCur: 0,
				scrollLeft: 0,
				tabs: ['消息列表', '通知'],

				modalName: null,
				listTouchStart: 0,
				listTouchDirection: null,

				chats: [
					{
							"name": "翻滚牛莽莽",
							"date": "2020-10-28 12:12",
							"desc": "购买了商品【 股权架构书 第一课时 N0.5 】"
						},
					{
							"name": "翻滚牛莽莽",
							"date": "2020-10-25 09:28",
							"desc": "购买了商品【 股权架构书 第一课时 N0.4 】"
						},
					{
						"name": "翻滚牛莽莽",
						"date": "2020-10-23 17:59",
						"desc": "购买了商品【 股权架构书 第一课时 N0.3 】"
					},
					{
						"name": "翻滚牛莽莽",
						"date": "2020-10-13 07:19",
						"desc": "购买了商品【 股权架构书 第一课时 N0.2 】"
					},
					{
						"name": "翻滚牛莽莽",
						"date": "2020-09-29 11:19",
						"desc": "购买了商品【 股权架构书 第一课时 N0.1 】"
					},
				]
			}
		},
		methods: {
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			// toChat(index) {
			// 	uni.navigateTo({
			// 		url: '/pages/main/chat'
			// 	})
			// },
			// ListTouch触摸开始
			ListTouchStart(e) {
				this.listTouchStart = e.touches[0].pageX
			},

			// ListTouch计算方向
			ListTouchMove(e) {
				this.listTouchDirection = e.touches[0].pageX - this.listTouchStart > 0 ? 'right' : 'left'
			},

			// ListTouch计算滚动
			ListTouchEnd(e) {
				if (this.listTouchDirection == 'left') {
					this.modalName = e.currentTarget.dataset.target
				} else {
					this.modalName = null
				}
				this.listTouchDirection = null
			},

			showModal(e) {
				this.modalName = e.currentTarget.dataset.target
			},
			hideModal(e) {
				this.modalName = null
			},
		}
	}
</script>

<style lang="scss">
	.m-notifications-list {
		.m-notifications-item {
			display: flex;
			align-items: center;
			justify-content: space-between;
			height: 200rpx;
			// border-bottom: 1px solid gray;

			.m-notification-left {
				display: flex;

				.m-detail {
					margin-left: 32rpx;

					.m-notif-title {
						color: #FFFFFF;
						margin-bottom: 8rpx;
					}

					.m-notif-detail {
						// color: ;
					}
				}
			}

			.m-notification-right {
				.m-thumb-wrapper {
					position: relative;
					width: 180rpx;
					height: 140rpx;
					margin-right: 32rpx;

					image {
						width: 100%;
						height: 100%;
						vertical-align: middle;
						border-radius: 16rpx;
					}

					text {
						position: absolute;
						top: 50rpx;
						left: 40%;
						color: rgba($color: #ffffff, $alpha: 0.8);
						width: 40rpx;
						height: 40rpx;
						border: 1px solid transparent;
						border-radius: 50%;
						display: flex;
						justify-content: center;
						align-items: center;

						background-color: rgba($color: #000000, $alpha: 0.6);
					}
				}
			}
		}
	}

	.m-settings {
		margin-right: 32rpx;
		font-size: 36rpx;
	}

	.cu-list.menu-avatar>.cu-item {
		width: 95%;
		padding: 0;
		margin: 20rpx auto;
		background-color: #21213C;
		.action{
			width: 160rpx;
		}
		.move{
			margin: 20rpx -20rpx;
		}
	}
</style>
