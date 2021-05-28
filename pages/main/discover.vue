<template>
	<view class="m-page m-main-bg" style="padding-bottom: 100rpx;">
		
		<view class="m-content" style="padding-top: 50rpx;">
			<view class="cu-bar search m-bar">
				<view class="m-title">
					<text>注塑之家</text>
					<text class="cuIcon-triangledownfill"></text>
				</view>
				<view class="search-form round" v-show="is_show_search">
					<text class="cuIcon cuIcon-">&nbsp;</text>
					<input :adjust-position="false" type="text" placeholder="搜索图片、文章、视频" confirm-type="search"></input>
				</view>
				<view class="flex align-center">
					<view class="cuIcon cuIcon-search m-search" @click="is_show_search = !is_show_search"></view>
					<view class="cu-avatar round" style="background-image:url('../../static/images/user.jpg')"></view>
				</view>
			</view>

			<view class="m-recommendations">
				<view class="m-recom-item" v-for="(item, index) in trends" :key="index" @click="toDetail()">
					<!-- <view class="m-thumbnail"  style="background-size: cover; background-repeat: no-repeat; background-position: 0;" :style="'background-image:url('+item.image+');'"> -->
						<view class="m-thumbnail">
							<img :src="item.image" mode=""></img>
							<text class="m-extra text-xs">{{item.extra}}</text>
							<view class="cuIcon cuIcon-play_forward_fill m-fav-play"></view>
					</view>
					<view class="m-recom-detail">
						<view class="m-recom-top">
							<view class="m-recom-title">{{item.title}}</view>
						</view>
						<view class="m-recom-bottom">
							<view class="m-recom-views">¥ {{item.price}} 元</view>
							<!-- <view class="m-recom-info-name">{{item.name}}</view> -->
							<view class="m-recom-info-sub">{{item.Sales}} 人已购买</view>
						</view>
					</view>
				</view>
			</view>

		</view>

	</view>
</template>

<script>
	export default {
		methods:{
			toDetail(){
				uni.navigateTo({
					url: '/pages/main/shipin'
				})
			}
		},
		data() {
			return {
				is_show_search: false,
				trends: [
					{"image": "../../static/images/Expand.jpg", "extra": "22:33", "title": "增资扩股协议书范本", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "11:22", "title": "有限责任公司增资扩股协议", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "新三板股权激励全解析-77个案例", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "有限公司溢价增资扩股协议书", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "增资扩股协议-完整版", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "增资扩股协议-模板", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "增资扩股协议书(推荐范本)", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "非上市公司股权激励模式及经典案例", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "公司增资扩股协议", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "某有限公司增资扩股方案", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "新三板股权激励案例分析", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "新三板实施股权激励操作要点", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "有限公司增资扩股方案计划", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "有限公司增资扩股协议书", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "有限责任公司增资扩股协议范本", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "增资扩股协议(范本)", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					{"image": "../../static/images/Expand.jpg", "extra": "44:99", "title": "(公司实例)增资扩股协议", "price": "9.99", "name": "注塑之家", "Sales": "12,255"},
					]
			}
		}
	}
</script>

<style lang="scss">
	@import "static/css/variables.scss";

	.m-bar {
		.m-title {
			font-size: 36rpx;
			font-weight: bold;
			color: $white;
		}

		.m-search {
			font-weight: bold;
			color: $white;
			margin-right: 16rpx;
			font-size: 32rpx;
		}
	}
	.m-recommendations{
		display: -webkit-box;
		display: -webkit-flex;
		display: flex;
		-webkit-flex-wrap: wrap;
		flex-wrap: wrap;
		-webkit-box-orient: horizontal;
		-webkit-box-direction: normal;
		-webkit-flex-direction: row;
		flex-direction: row;
		-webkit-box-align: center;
		-webkit-align-items: center;
		align-items: center;
		-webkit-box-pack: justify;
		-webkit-justify-content: space-between;
		justify-content: space-between;
		.m-recom-item{
			width: 48%;
			height: auto;
			margin: 20rpx 0rpx;
			padding: 0px;
			display: -webkit-box;
			display: -webkit-flex;
			display: flex;
			-webkit-box-orient: vertical;
			-webkit-box-direction: normal;
			-webkit-flex-direction: column;
			flex-direction: column;
			overflow: hidden;
			.m-thumbnail{
				position: relative;
				width: 100%;
				height: 100%;
				margin-bottom: 32rpx;
				img{
					width: auto;
					height: auto;
					max-width: 100%;
					max-height: 100%;
					vertical-align: middle;
					border-radius: 8rpx;
				}
				.m-extra{
					position: absolute;
					top: 5%;
					right: 5%;
					padding: 10rpx;
					color: $white;
					display: flex;
					justify-content: center;
					align-items: center;
					border-radius: 8rpx;
					background-color: rgba($color: #000000, $alpha: 0.8);
				}
				.m-fav-play{
					position: absolute;
					top: 20%;
					left: 35%;
					color: rgba($color: #ffffff, $alpha: 0.8);
					width: 100rpx;
					height: 100rpx;
					padding: 20rpx;
					border: 1rpx solid transparent;
					border-radius: 50%;
					display: flex;
					justify-content: center;
					align-items: center;
					background-color: rgba($color: #000000, $alpha: 0.6);
					
				}
			}
			.m-recom-detail{
				align-items: center;
				justify-content: space-between;
				.m-recom-top{
					width: 100%;
					.m-recom-title{
						width: 100%;
						height: 80rpx;
						color: $white !important;
						font-weight: 500;
						font-size: 28rpx;
						overflow:hidden; 
						text-overflow:ellipsis;
						display:-webkit-box; 
						-webkit-box-orient:vertical;
						-webkit-line-clamp:2; 
					}
				}
				.m-recom-bottom{
					display: -webkit-box;
					display: -webkit-flex;
					display: flex;
					-webkit-flex-wrap: wrap;
					flex-wrap: wrap;
					// .m-recom-info-name{
					// 	color: $white !important;
					// 	font-weight: 500;
					// 	font-size: 24rpx;
					// 	margin-bottom: 16rpx;
					// }
					.m-recom-views{
						color: $pink !important;
						font-size: 22rpx;
					}
					.m-recom-info-sub{
						color: $gray !important;
						font-size: 18rpx;
						flex: 1;
						text-align: right;
					}
				}
			}
		}
	}
</style>
