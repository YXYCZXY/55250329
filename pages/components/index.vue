<template>
    <view class="uni-tabbar">
        <view class="uni-tabbar__item" v-for="(item, index) in tabbar" :key="index" @tap="changeTab(item)">
            <view class="uni-tabbar__bd">
                <view :class="['uni-tabbar__icon', { bounce: item.pagePath === currentPage }]">
                    <img v-if="item.pagePath === pagePath" class="uni-w-42 uni-h-42" :src="item.selectedIconPath" />
                    <img v-else class="uni-w-42 uni-h-42" :src="item.iconPath" />
                </view>
            </view>
            <view class="uni-tabbar__label">
                {{ item.text }}
            </view>
        </view>
    </view>
</template>

<script>
export default {
    props: {
        pagePath: String
    },
    data() {
        return {
            currentPage: this.pagePath,
            tabbar: [
                {
                    pagePath: "/pages/Monster/index",
                    iconPath: "/static/bar-gs.png",
                    selectedIconPath: "/static/bar-gs.png",
                    text: "",
                },
                {
                    pagePath: "/pages/Masa/index",
                    text: "",
                    iconPath: "/static/bar-ms.png",
                    selectedIconPath: "/static/bar-ms.png"
                },
                {
                    pagePath: "/pages/Ashin/index",
                    text: "",
                    iconPath: "/static/bar-as.png",
                    selectedIconPath: "/static/bar-as.png"
                },
                {
                    pagePath: "/pages/Stone/index",
                    text: "",
                    iconPath: "/static/bar-st.png",
                    selectedIconPath: "/static/bar-st.png"
                },
                {
                    pagePath: "/pages/Ming/index",
                    text: "",
                    iconPath: "/static/bar-gy.png",
                    selectedIconPath: "/static/bar-gy.png"
                }
            ]
        };
    },
    watch: {
        pagePath(newPath) {
            this.currentPage = newPath;
        }
    },
    methods: {
        changeTab(item) {
            this.currentPage = item.pagePath;
            uni.showLoading({
                title: '正在加载...'
            });

            uni.switchTab({
                url: item.pagePath,
                success: () => {
                    uni.hideLoading();
                },
                fail: (e) => {
                    console.log(e);
                }
            });
        }
    }
}
</script>

<style lang="scss" scoped>
@keyframes bounce {
    0%, 20%, 50%, 80%, 100% {
        transform: translateY(0);
    }
    40% {
        transform: translateY(-30px);
    }
    60% {
        transform: translateY(-15px);
    }
}

.uni-tabbar {
    z-index: 999;
    width: 100%;
    height: 6%;
    display: flex;
    justify-content: space-around;
    padding: 7rpx 0;
    box-sizing: border-box;
    box-shadow: 0px 10px 20px 0px rgba(75, 51, 100, 0.05);

    .uni-tabbar__item {
        display: flex;
        flex-direction: column;

        .uni-tabbar__bd {
            .uni-tabbar__icon {
                width: 100rpx;
                height: 100rpx;
                img {
                    width: 100%;
                    height: 100%;
                }
                &.bounce {
                    animation: bounce 1s infinite;
                }
            }
        }

        .uni-tabbar__label {
            font-size: 22rpx;
            font-weight: 400;
            color: #D8DCE7;
            text-align: center;
            &.active {
                background-image: linear-gradient(to right top, #1CFDF1, #B330FF);
                font-size: 22rpx;
                -webkit-background-clip: text;
                -moz-background-clip: text;
                background-clip: text;
                box-decoration-break: clone;
                -webkit-box-decoration-break: clone;
                -moz-box-decoration-break: clone;
                color: transparent;
                position: relative;
            }
        }
    }

    .icon {
        display: inline-block;
    }
}
</style>
