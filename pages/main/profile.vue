<template>
	<view class="m-page m-main-bg" style="padding-bottom: 100rpx;">
		<view class="m-fixed">
			<cu-custom :isBack="true" bgColor="bg-shadeTop text-white">
				<block slot="backText"></block>
				<block slot="content">我</block>
				<block slot="right">
					<view class="cuIcon cuIcon-settingsfill m-settings" @click="toSettings()"></view>
				</block>
			</cu-custom>
		</view>
		<view class="profile">
			<view class="m-avatar">
				<image src="../../static/images/user.jpg" mode=""></image>
			</view>
			<view class="m-username">注塑之家</view>
				<view class="informations">
					<view class="info-item" v-for="(item, index) in informations" :key="index" :class="index==Object.keys(informations).length - 1? '':'not-last'">
						<view class="data">{{item.data}}</view>
						<view class="title">{{item.title}}</view>
					</view>
				</view>
			</view>
		<view class="m-content">
			
				<scroll-view scroll-x class="nav">
					<view class="flex text-center">
						<view class="cu-item flex-sub m-tab" :class="index==TabCur?'m-tab-selected cur':''" v-for="(item,index) in tabs" :key="index" @tap="tabSelect" :data-id="index">
							{{item}}
						</view>
					</view>
				</scroll-view>
				
				<view class="m-thumbs-list">
					<view class="m-cover-item" v-for="(item, index) in vids">
						<view class="flex">
							<view class="m-thumb">
								<image :src="item.image" mode=""></image>
							</view>
							<view class="m-content">
								<view class="m-title">{{item.title}}</view>
								<view class="m-data">{{item.data}} 人浏览</view>
							</view>
						</view>
						<view class="cuIcon cuIcon-moreandroid m-text-white"></view>
					</view>
				</view>
			
		</view>
		</view>
</template>

<script>
	export default{
		data(){
			return{
				TabCur: 0,
				scrollLeft: 0,
				tabs:['我的视频', '商品', '数据', '关注'],
				informations: [
					{"title": "视频", "data": "45"},
					{"title": "观看", "data": "12万"},
					{"title": "关注", "data": "22"},
					{"title": "粉丝", "data": "3万"},
				],
				vids: [
					{"image": "../../static/images/Expand.jpg", "title": "股权架构书 第一课时 NO.1", "data": "122.567"},
					{"image": "../../static/images/Excitation.jpg", "title": "股权架构书 第一课时 NO.2", "data": "34,222"},
					{"image": "../../static/images/Reform.jpg", "title": "股权架构书 第一课时 NO.3", "data": "854,895"},
					{"image": "../../static/images/Transfer.jpg", "title": "股权架构书 第一课时 NO.4", "data": "123,432"},
					{"image": "../../static/images/Financing.jpg", "title": "股权架构书 NO.5", "data": "2,000"},
					{"image": "../../static/images/Register.jpg", "title": "股权架构书 NO.6", "data": "2,000"},
				]
			}
		},
		methods:{
			tabSelect(e) {
				this.TabCur = e.currentTarget.dataset.id;
				this.scrollLeft = (e.currentTarget.dataset.id - 1) * 60
			},
			
			toSettings(){
				uni.navigateTo({
					url: '/pages/main/settings'
				})
			}
		}
	}
</script>

<style lang="scss">
	@import  "static/css/variables.scss";
	.profile{
		display: flex;
		flex-direction: column;
		justify-content: center;
		background-image: linear-gradient(transparent, #111230 100%), url(../../static/images/bg-music.jpeg);
		// background-image: url(../../static/images/bg-music.jpeg);
		background-size: cover;
		margin-bottom: 32rpx;
		padding: 0 32rpx;
		.m-avatar{
			width: 240rpx;
			height: 240rpx;
			margin: 180rpx 0 32rpx 0;
			align-self: center;
			image{
				width: 100%;
				height: 100%;
				vertical-align: middle;
				border-radius: 50%;
			}
		}
		.m-username{
			color: $white !important;
			font-size: 64rpx;
			align-self: center;
			margin-bottom: 32rpx;
			font-weight: 500;
		}
	}
	.informations{
		display: flex;
		flex-direction: row;
		align-items: center;
		justify-content: space-between;
		.info-item{
			display: flex;
			flex-direction: column;
			margin: 16rpx;
			padding: 0 16rpx;
			align-items: center;
			.data{
				color: $white !important;
				font-weight: bolder;
				margin-bottom: 8rpx;
			}
			.title{
				color: $gray !important;
				font-weight: lighter;
			}
		}
		.not-last{
			// border-right: 1px solid $gray;
		}
	}
	.m-settings{
		margin-right: 32rpx;
		font-size: 36rpx;
	}
	
	
</style>
