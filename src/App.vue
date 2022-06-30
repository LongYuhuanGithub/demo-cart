<template>
    <div class="app-container">
        <!-- Header 头部区域 -->
        <Header />

        <!-- 渲染购物车列表 -->
        <Goods v-for="item in cartList" :key="item.id" />
    </div>
</template>

<style lang="less" scoped>
    .app-container {
        padding-top: 45px;
        padding-bottom: 50px;
    }
</style>

<script>
    // 导入 axios 请求库
    import axios from "axios";

    // 导入需要的组件
    import Header from "@/components/Header/Header.vue";
    import Goods from "@/components/Goods/Goods.vue";

    export default {
        created() {
            this.initCartList();
        },
        data() {
            return {
                cartList: [], // 购物车列表
            };
        },
        methods: {
            async initCartList() {
                const { data } = await axios.get("https://www.escook.cn/api/cart");
                if (data.status === 200) this.cartList = data.list;
            },
        },
        components: {
            Header,
            Goods,
        },
    };
</script>