<template>
    <div class="manage_page fillcontain">
        <el-row style="height: 100%;">
            <el-col :span="4" style="min-height: 100%; background-color: #324057;">
                <!-- default-actinve定义了每次默认展开的menu，这里使用$router.path来映射当前router和被选择菜单
                即每个el-menu-item中的index属性值与$router.path相同
                router属性使用 vue-router 的模式，启用该模式会在激活导航时以 index 作为 path 进行路由跳转 -->
                <el-menu :default-active="defaultActive" style="min-height: 100%;" theme="dark" unique-opened router>
                    <el-menu-item index="manage">
                        <i class="el-icon-menu"></i>首页</el-menu-item>
                    <el-submenu index="2">
                        <template slot="title">
                            <i class="el-icon-document"></i>数据管理
                        </template>
                        <el-menu-item index="">工人列表</el-menu-item>
                        <el-menu-item index="">管道列表</el-menu-item>
                        <el-menu-item index="">项目列表</el-menu-item>
                        <el-menu-item index="adminList">管理员列表</el-menu-item>
                        <!-- <el-menu-item index="userList">用户列表</el-menu-item>
                        <el-menu-item index="shopList">商家列表</el-menu-item>
                        <el-menu-item index="foodList">食品列表</el-menu-item>
                        <el-menu-item index="orderList">订单列表</el-menu-item>
                        <el-menu-item index="adminList">管理员列表</el-menu-item> -->
                    </el-submenu>
                    <el-submenu index="3">
                        <template slot="title">
                            <i class="el-icon-plus"></i>添加数据
                        </template>
                        <el-menu-item index="">添加工人</el-menu-item>
                        <el-menu-item index="">添加管道</el-menu-item>
                        <el-menu-item index="">添加项目</el-menu-item>
                        <!-- <el-menu-item index="addShop">添加商铺</el-menu-item>
                        <el-menu-item index="addGoods">添加商品</el-menu-item> -->
                    </el-submenu>
                    <el-submenu index="4">
                        <template slot="title">
                            <i class="el-icon-star-on"></i>可视化分析
                        </template>
                        <el-menu-item index="">管道分布</el-menu-item>
                        <el-menu-item index="">项目进展</el-menu-item>
                        <el-menu-item index="">自定义分析</el-menu-item>
                        <!-- <el-menu-item index="visitor">用户分布</el-menu-item> -->
                        <!-- <el-menu-item index="newMember">用户数据</el-menu-item> -->
                    </el-submenu>
                    <!-- <el-submenu index="5">
                        <template slot="title">
                            <i class="el-icon-edit"></i>编辑
                        </template>
                        <el-menu-item index="uploadImg">上传图片</el-menu-item>
                        <el-menu-item index="vueEdit">文本编辑</el-menu-item>
                    </el-submenu> -->
                    <el-submenu index="5">
                        <template slot="title">
                            <i class="el-icon-setting"></i>设置
                        </template>
                        <el-menu-item index="adminSet">管理员设置</el-menu-item>
                        <!-- <el-menu-item index="sendMessage">发送通知</el-menu-item> -->
                    </el-submenu>
                    <el-submenu index="6">
                        <template slot="title">
                            <i class="el-icon-warning"></i>说明
                        </template>
                        <el-menu-item index="explain">说明</el-menu-item>
                    </el-submenu>
                </el-menu>
            </el-col>
            <el-col :span="20" style="height: 100%;overflow: auto;">
                <!-- 在组件切换过程中将状态保留在内存中，防止重复渲染DOM。和 <transition> 相似，<keep-alive> 是一个抽象组件：它自身不会渲染一个 DOM 元素，也不会出现在父组件链中。 -->
                <keep-alive>
                    <router-view></router-view>
                </keep-alive>
            </el-col>
        </el-row>
    </div>
</template>

<script>
    export default {
        //   data() {
        //     return {
        //       isCollapse: true
        //     };
        //   },
        //   methods: {
        //     handleOpen(key, keyPath) {
        //       console.log(key, keyPath);
        //     },
        //     handleClose(key, keyPath) {
        //       console.log(key, keyPath);
        //     }
        //   },
        computed: {
            defaultActive: function () {
                return this.$route.path.replace("/", "");
            }
        }
    };

</script>


<style lang="less" scoped>
    @import "../style/mixin";

    // .el-menu-vertical-demo:not(.el-menu--collapse) {
    //   width: 200px;
    //   min-height: 400px;
    // }

</style>
