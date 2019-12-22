//"数据管理"界面
<template>
    <div class="crumbs">
        <el-breadcrumb separator="/">
            <el-breadcrumb-item><i class="el-icon-rank"></i>数据管理</el-breadcrumb-item>
            <el-breadcrumb-item><i class="el-icon-lx-cascades"></i> 历史数据管理</el-breadcrumb-item>
        </el-breadcrumb>
    </div>
</template>

<script>
    //export default 用法大多用在单页面应用内，基于一系列脚手架
    export default {
        data(){
            return {
                visible: false
            }
        }
    }
</script>

<style scoped>

</style>