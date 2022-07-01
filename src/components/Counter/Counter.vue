<template>
    <div class="number-container d-flex justify-content-center align-items-center">
        <!-- 减 1 的按钮 -->
        <button type="button" class="btn btn-light btn-sm" @click="countChange(false)">-</button>
        <!-- 购买的数量 -->
        <span class="number-box">{{ count }}</span>
        <!-- 加 1 的按钮 -->
        <button type="button" class="btn btn-light btn-sm" @click="countChange(true)">+</button>
    </div>
</template>

<style lang="less" scoped>
    .number-box {
        margin: 0 5px;
        min-width: 30px;
        text-align: center;
        font-size: 12px;
    }

    .btn-sm {
        width: 30px;
    }
</style>

<script>
    export default {
        props: {
            count: { default: 1, type: Number },
        },
        methods: {
            // 监听商品数量改变
            countChange(flag) {
                if (flag) {
                    this.$emit("count-change", this.count + 1);
                } else if (this.count > 1) this.$emit("count-change", this.count - 1);
            },
        },
    };
</script>