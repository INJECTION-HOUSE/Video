<template>
	<view class="m-page m-main-bg" style="padding-bottom: 100rpx;">
		<view class="m-paral">
			<view class="m-infos">
				<!-- <view class="m-top-text">
					Best Album Ever <text class="cuIcon cuIcon-upstagefill text-yellow margin-left-sm"></text>
				</view>
				<view class="m-middle-text" @click="toDetail()">
					为千万注塑企业保驾护航
				</view>
				<view class="m-bottom-text">
					<text>注塑之家</text><text>注塑淘</text><text>玩注塑</text>
				</view> -->
				<view class="m-mini-info">
					<view class="m-left">
						<view class="cu-avatar round margin-right-sm" style="background-image:url('../../static/images/user.jpg')"></view>
						<view class="content">
							<view class="m-name">注塑之家</view>
							<view class="m-data">32万粉丝</view>
						</view>
					</view>
					<view class="m-right">125万 次观看</view>
				</view>
			</view>
		</view>
		<view class="m-content">
			<view class="m-buttons">
				<view class="flex justify-between">
					<view class="margin-tb-sm text-center" v-for="(item,index) in buttons" :key="index">
						<button class="cu-btn round" :class="" >
							<text :style="'color:'+item.color" class="cuIcon margin-right-xs" :class="'cuIcon-'+item.icon"></text>
							{{item.data}}
							</button>
					</view>
				</view>
			</view>
			<view class="m-discover">
				<view class="m-title">
					<text class="cuIcon cuIcon-search margin-right-sm"></text>发现
				</view>
				<scroll-view scroll-x class="flex" >
					<view class="flex">
						<view v-for="(item,index) in discovers" :key="index" class="m-object" @click="toDetail()">
							<view class="m-thumb">
								<image :src="item.image" mode="aspectFill"></image>
							</view>
							<view class="m-title">{{item.title}}</view>
							<view class="m-data">{{item.data}}</view>
						</view>
					</view>
					
				</scroll-view>
			</view>
			<view class="m-discover">
				<view class="m-title">
					<text class="cuIcon cuIcon-search margin-right-sm"></text>猜你喜欢
				</view>
				<view class="m-fav-list">
					<view class="m-fav" v-for="(item,index) in discovers" :key="index" @click="toDetail()">
						<view class="m-fav-top flex justify-between align-center">
							<view class="m-fav-top-left flex justify-start">
								<view class="cu-avatar round margin-right-sm" style="background-image:url('../../static/images/user.jpg')"></view>
								<view class="m-fav-left-right">
									<view class="m-name">注塑之家</view>
									<view class="m-slogan">{{item.title}}</view>
								</view>
							</view>
							<view class="m-fav-top-right">
								<view class="cuIcon cuIcon-moreandroid m-more-android"></view>
							</view>
						</view>
						<view class="m-fav-middle">
							<image :src="item.image" mode="aspectFill"></image>
							<view class="cuIcon cuIcon-play_forward_fill m-fav-play"></view>
						</view>
						<view class="m-fav-bottom flex align-center">
							<button class="cu-btn m-c-btn" >
								<text class="cuIcon margin-right-xs cuIcon-likefill m-text-pink"></text>
								442
								</button>
								<view class="cu-avatar-group">
									<view class="cu-avatar round sm" v-for="(item,index) in avatar" :key="index" :style="[{ backgroundImage:'url(' + avatar[index] + ')' }]"></view>
								</view>
								<view class="" style="margin-left: auto;">
									<button class="cu-btn m-c-btn">
										<text class="cuIcon cuIcon-commentfill margin-right-xs m-text-gray"></text>
										25
										</button>
								</view>
						</view>
					</view>
				</view>
				
			</view>
		</view>
		
	</view>
</template>

<script>
	export default{
		data(){
			return{
				buttons: [
					{"icon": "likefill", "data": "8万", "color": "#FF3465"},
					{"icon": "evaluate_fill", "data": "1万", "color": ""},
					{"icon": "share", "data": "657", "color": ""},
					// {"icon": "commentfill", "data": "106", "color": ""}
				],
				discovers: [
					{"image": "../../static/images/Expand.jpg", "title": "股权架构书 NO.1", "data": "2000 次观看"},
					{"image": "../../static/images/Excitation.jpg", "title": "股权架构书 NO.2", "data": "2000 次观看"},
					{"image": "../../static/images/Reform.jpg", "title": "股权架构书 NO.3", "data": "2000 次观看"},
					{"image": "../../static/images/Transfer.jpg", "title": "股权架构书 NO.4", "data": "2000 次观看"},
					{"image": "../../static/images/Financing.jpg", "title": "股权架构书 NO.5", "data": "2000 次观看"},
					{"image": "../../static/images/Register.jpg", "title": "股权架构书 NO.6", "data": "2000 次观看"},
				],
				avatar: [
					'https://ossweb-img.qq.com/images/lol/web201310/skin/big10001.jpg',
					'https://ossweb-img.qq.com/images/lol/web201310/skin/big81005.jpg',
					'https://ossweb-img.qq.com/images/lol/web201310/skin/big25002.jpg',
					'https://ossweb-img.qq.com/images/lol/web201310/skin/big91012.jpg'
				],
			}
			
		},
		methods:{
			toDetail(){
				uni.navigateTo({
					url: '/pages/main/shipin'
				})
			}
		}
	}
</script>

<style lang="scss">
	@import  "static/css/variables.scss";
	.m-fav-list{
		.m-fav{
			margin-bottom: 64rpx;
			.m-fav-top{
				margin-bottom: 32rpx;
				.m-fav-left-right{
					.m-name{
						color: $white;
						margin-bottom: 10rpx;
						font-weight: bold;
					}
					.m-slogan{
						color: $gray;
						font-weight: lighter;
					}
				}
				.m-fav-top-right{
					color: $white;
				}
			}
			.m-fav-middle{
				position: relative;
				width: 100%;
				height: 400rpx;
				margin-bottom: 32rpx;
				image{
					width: 100%;
					height: 100%;
					vertical-align: middle;
					border-radius: 16rpx;
				}
				.m-fav-play{
					position: absolute;
					top: 40%;
					left: 40%;
					color: rgba($color: #ffffff, $alpha: 0.8);
					font-size: 48rpx;
					width: 98rpx;
					height: 98rpx;
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
	.m-search{
		font-size: 48rpx;
		font-weight: bolder;
		color: $white;
	}
	.m-paral{
		// height: 350px;
		// position: relative;
		padding-top: 100rpx;
		z-index: 0;
		background-image: linear-gradient(transparent, #111230 90%), url(../../static/images/zhusuzhijia.jpg);
		background-size: cover;
		background-repeat: no-repeat;
		image{
			position: absolute;
			z-index: -1;
			left: 0;
			right: 0;
			bottom: 0;
			right: 0;
			width: 100%;
			height: 100%;
		}
		.m-infos{
			// position: absolute;
			z-index: 1;
			padding-top: 200rpx;
			margin: 0 32rpx;
			// top: 25%;
			// left: 32rpx;
			.m-top-text{
				color: $white;
				margin-bottom: 16rpx;
				font-size: 24rpx;
				font-weight: 300;
			}
			.m-middle-text{
				color: $white;
				margin-bottom: 32rpx;
				font-size: 64rpx;
				font-weight: 700;
				width: 70%;
				letter-spacing: 2;
			}
			.m-bottom-text{
				color: $white;
				margin-bottom: 32rpx;
				font-size: 32rpx;
				font-weight: 300;
				width: 60%;
				letter-spacing: 2;
				text{
					margin-right: 16rpx;
				}
			}
			
		}
	}
	
	.m-discover{
		margin-bottom: 64rpx;
		.m-title{
			color: $white !important;
			font-size: 36rpx;
			font-weight: bolder;
			margin-bottom: 32rpx;
		}
	}
	.m-object{
		display: flex;
		flex-direction: column;
		width: 350rpx;
		// height: 300rpx;
		margin-right: 32rpx;
		.m-thumb{
			width: 350rpx;
			height: 300rpx;
			margin-bottom: 32rpx;
			image{
				width: 100%;
				height: 100%;
				vertical-align: middle;
				border-radius: 4px;
			}
		}
		.m-title{
			color: $white !important;
			font-size: 32rpx;
			margin-bottom: 16rpx;
		}
		.m-data{
			color: $gray !important;
		}
	}
	.m-c-btn{
		background-color: rgba($color: #727D8D, $alpha: 0.3);
		color: $gray;
		padding: 0;
		padding: 8rpx 24rpx;
		border-radius: 16rpx;
	}
</style>
