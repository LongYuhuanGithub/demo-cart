<template>
    <div class="footer-container">
        <!-- 左侧的全选 -->
        <div class="custom-control custom-checkbox">
            <input type="checkbox" class="custom-control-input" id="cbFull" :checked="true" />
            <label class="custom-control-label" for="cbFull">全选</label>
        </div>

        <!-- 中间的合计 -->
        <div>
            <span>合计：</span>
            <span class="total-price">￥{{ 0 }}</span>
        </div>

        <!-- 结算按钮 -->
        <button type="button" class="btn btn-primary btn-settle">
            结算（{{ 0 }}）
        </button>
    </div>
</template>

<style lang="less" scoped>
    .footer-container {
        position: fixed;
        bottom: 0;
        display: flex;
        justify-content: space-between;
        align-items: center;
        border-top: 1px solid #efefef;
        padding: 0 10px;
        font-size: 12px;
        height: 50px;
        width: 100%;
        background-color: #fff;
    }

    .custom-checkbox {
        display: flex;
        align-items: center;
    }

    #cbFull {
        margin-right: 5px;
    }

    .btn-settle {
        border-radius: 25px;
        height: 80%;
        min-width: 110px;
        font-size: 12px;
    }

    .total-price {
        font-weight: bold;
        font-size: 14px;
        color: red;
    }
</style>

<script>
    export default {};
</script>