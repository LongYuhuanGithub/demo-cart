<template>
    <div class="number-container d-flex justify-content-center align-items-center">
        <!-- 减 1 的按钮 -->
        <button type="button" class="btn btn-light btn-sm">-</button>
        <!-- 购买的数量 -->
        <span class="number-box">1</span>
        <!-- 加 1 的按钮 -->
        <button type="button" class="btn btn-light btn-sm">+</button>
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
    export default {};
</script>