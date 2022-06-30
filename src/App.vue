<template>
    <div class="app-container">
        <!-- Header 头部区域 -->
        <Header />

        <!-- 渲染购物车列表 -->
        <Goods
            v-for="item in cartList"
            :key="item.id"
            :id="item.id"
            :img="item.goods_img"
            :name="item.goods_name"
            :price="item.goods_price"
            :state="item.goods_state"
            @state-change="stateChange"
        />

        <!-- Footer 底部区域 -->
        <Footer />
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
    import Footer from "@/components/Footer/Footer.vue";

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
            // 监听 Goods 子组件的复选框改变
            stateChange(obj) {
                this.cartList.some(item => {
                    if (item.id === obj.id) {
                        item.goods_state = obj.state;
                        return true;
                    }
                });
            },
        },
        // 计算属性
        computed: {
            // 计算出是否全选
            fullState() {
                return this.cartList.every(item => item.goods_state);
            },
        },
        components: {
            Header,
            Goods,
            Footer,
        },
    };
</script>