<template>
    <div class="goods-container">
        <!-- 左侧图片 -->
        <div class="thumb">
            <div class="custom-control custom-checkbox">
                <!-- 复选框 -->
                <input type="checkbox" class="custom-control-input" :id="'goods' + id" :checked="state" @change="stateChange" />
                <label class="custom-control-label" :for="'goods' + id">
                    <!-- 商品的缩略图 -->
                    <img :src="img" alt="" />
                </label>
            </div>
        </div>
        <!-- 右侧信息区域 -->
        <div class="goods-info">
            <!-- 商品标题 -->
            <h6 class="goods-title">{{ name }}</h6>
            <div class="goods-info-bottom">
                <!-- 商品价格 -->
                <span class="goods-price">￥{{ price }}</span>
                <!-- 商品的数量 -->
                <slot />
            </div>
        </div>
    </div>
</template>

<style lang="less" scoped>
    .goods-container {
        + .goods-container {
            border-top: 1px solid #efefef;
        }
        
        display: flex;
        padding: 10px;

        .thumb {
            display: flex;
            align-items: center;

            img {
                width: 100px;
                height: 100px;
                margin: 0 10px;
            }
        }

        .goods-info {
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            flex: 1;

            .goods-title {
                font-weight: bold;
                font-size: 12px;
            }

            .goods-info-bottom {
                display: flex;
                justify-content: space-between;

                .goods-price {
                    font-weight: bold;
                    color: red;
                    font-size: 13px;
                }
            }
        }
    }
</style>

<script>
    export default {
        props: {
            id: { type: Number, require: true },
            img: { default: "", type: String },
            name: { default: "", type: String },
            price: { default: 0, type: Number },
            state: { default: true, type: Boolean },
        },
        methods: {
            // 监听复选框改变
            stateChange(event) {
                this.$emit("state-change", {
                    id: this.id,
                    state: event.target.checked,
                });
            },
        },
    };
</script>