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
            :count="item.goods_count"
            @state-change="stateChange"
        />

        <!-- Footer 底部区域 -->
        <Footer :fullState="fullState" :amount="amount" @full-change="fullChange" />
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
            // 监听 Footer 子组件的全选状态改变
            fullChange(val) {
                this.cartList.forEach(item => item.goods_state = val);
            },
        },
        // 计算属性
        computed: {
            // 计算出是否全选
            fullState() {
                return this.cartList.every(item => item.goods_state);
            },
            // 计算已勾选商品的总价
            amount() {
                return this.cartList.filter(item => item.goods_state).reduce((total, item) => total += item.goods_price * item.goods_count, 0);
            },
        },
        components: {
            Header,
            Goods,
            Footer,
        },
    };
</script>