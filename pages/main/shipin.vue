<template>
	<view class="m-page m-main-bg">
		<view class="m-fixed">
			<cu-custom :isBack="true" bgColor="bg-shadeTop text-white">
				<block slot="backText"></block>
				<block slot="content"></block>
			</cu-custom>
		</view>
		<view class="m-video">
			<video src="../../static/video/DouYin.mp4" autoplay="true" controls></video>
		</view>
		<view class="m-hr"></view>
		<view class="m-content">
			<view class="m-video-info">
				<view class="m-info">
					<view class="m-title">
						股权加购书 NO.1
					</view>
					<view class="m-date">
						2020-11-21 12:09
					</view>
				</view>
				<view class="m-views">
					184万次观看
				</view>
			</view>
			<view class="m-buttons">
				<view class="flex justify-between">
					<view class="margin-tb-sm text-center" v-for="(item,index) in buttons" :key="index">
						<button class="cu-btn round" :class="">
							<text :style="'color:'+item.color" class="cuIcon margin-right-xs" :class="'cuIcon-'+item.icon"></text>
							{{item.data}}
						</button>
					</view>
				</view>
			</view>
			<view class="m-hr"></view>
			<view class="m-mini-info">
				<view class="m-left">
					<view class="cu-avatar round margin-right-sm" style="background-image:url('../../static/images/user.jpg')"></view>
					<view class="content">
						<view class="m-name">注塑之家</view>
						<view class="m-data">32万粉丝</view>
					</view>
				</view>
				<view class="m-right">
					<view class="m-follow">
						+ 关注
					</view>
				</view>
			</view>
			<scroll-view scroll-x class="nav">
				<view class="flex text-center">
					<view class="cu-item flex-sub m-tab" :class="index==TabCur?'m-tab-selected cur':''" v-for="(item,index) in tabs"
					 :key="index" @tap="tabSelect" :data-id="index">
						{{item}}
					</view>
				</view>
			</scroll-view>
			<view class="m-thumbs-list" v-show="TabCur==0">
				<view class="m-cover-item radius" v-for="(item, index) in vids" :key="index">
					<view class="flex">
						<view class="m-thumb">
							<image :src="item.image" mode=""></image>
						</view>
						<view class="m-content">
							<view class="m-title">{{item.title}}</view>
							<view class="m-data">{{item.data}} 人购买</view>
						</view>
					</view>
					<view class="flex flex-direction justify-center" style="align-self: center;">
						<text class="m-duration">¥ {{item.price}} 元</text>
						<button class="m-buy">立即购买</button>
					</view>
				</view>
			</view>
			
			<view class="m-thumbs-list" v-show="TabCur==1">
				<view class="m-cover-item  radius" v-for="(item, index) in details" :key="index">
					<view class="m-content">
						<view class="m-title text-lg">{{item.title}}</view>
						<view class="m-details margin-top text-xs">{{item.details}}</view>
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
				tabs: ['视频商品', '详情'],
				buttons: [{
						"icon": "likefill",
						"data": "8万",
						"color": "#FF3465"
					},
					{
						"icon": "evaluate_fill",
						"data": "1万",
						"color": ""
					},
					{
						"icon": "share",
						"data": "657",
						"color": ""
					},
					// {
					// 	"icon": "commentfill",
					// 	"data": "106",
					// 	"color": ""
					// }
				],
				vids: [{
						"image": "../../static/images/Expand.jpg",
						"title": "股权架构书 第一课时 NO.1",
						"data": "122.567",
						"price": "9.99"
					},
					{
						"image": "../../static/images/Excitation.jpg",
						"title": "股权架构书 第一课时 NO.2",
						"data": "34,222",
						"price": "9.99"
					},
					{
						"image": "../../static/images/Reform.jpg",
						"title": "股权架构书 第一课时 NO.3",
						"data": "854,895",
						"price": "9.99"
					},
					{
						"image": "../../static/images/Transfer.jpg",
						"title": "股权架构书 第一课时 NO.4",
						"data": "123,432",
						"price": "8.99"
					}
				],
				details: [{
						"title": "债权转股权是什么？",
						"details": "债权转股权是什么？债权转股权，是指债权人以其依法享有的对在中国境内设立的有限责任公司或者股份有限公司的债权，转为公司股权，增加公司注册资本的行为。债权转股权</br>管理规定：",
					}
				]

			}
		},
		methods: {
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			}
		}
	}
</script>

<style lang="scss">
	@import "static/css/variables.scss";

	.m-follow {
		color: $white !important;
		background-color: $pink !important;
		padding: 16rpx 32rpx;
		border-radius: 16rpx;
	}

	.m-video {
		width: 100%;
		height: 640rpx;

		video {
			width: 100%;
			height: 100%;

		}
	}

	.m-video-info {
		display: flex;
		// align-items: center;
		justify-content: space-between;
		color: $white;
		margin-bottom: 32rpx;

		.m-title {
			font-weight: 700;
			font-size: 32rpx;
			margin-bottom: 16rpx;
		}

		.m-date {
			color: $gray;
			font-weight: 300;
		}
	}
	
	.m-details{
		color: $white;
		line-height: 60rpx;
		text-indent: 28rpx;
		letter-spacing: 2rpx;
	}
	.m-duration {
		color: $pink;
		margin-right: 0rpx;
		margin-bottom: 20rpx;
		text-align: center;
	}

	.m-buy {
		display: flex;
		padding: 0rpx;
		align-items: center;
		justify-content: center;
		width: 140rpx;
		height: 48rpx;
		line-height: 48rpx;
		font-size: 24rpx;
		color: $pink;
		font-weight: bolder;
		border: 1px solid $pink;
		background: none;
	}
</style>
