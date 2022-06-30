<template>
    <div class="app-container">
        <!-- Header 头部区域 -->
        <Header />
    </div>
</template>

<style lang="less" scoped>
    .app-container {
        padding-top: 45px;
        padding-bottom: 50px;
    }
</style>

<script>
    import Header from "@/components/Header/Header.vue";

    export default {
        components: {
            Header,
        },
    };
</script>