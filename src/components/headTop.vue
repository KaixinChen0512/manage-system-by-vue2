<template>
    <div class="header_container">
		<!-- 面包屑，循环遍历router中的各个路由的meta信息作为路径 -->
		<el-breadcrumb separator=">">
			<el-breadcrumb-item :to="{ path: '/manage' }">首页</el-breadcrumb-item>
			<el-breadcrumb-item v-for="(item, index) in $route.meta" key="index">{{item}}</el-breadcrumb-item>
		</el-breadcrumb>
		<el-dropdown @command="handleCommand" menu-align='start' trigger="click">
			<!-- <img :src="baseImgPath + adminInfo.avatar" class="avator"> -->
      <span class="el-dropdown-link"><i class="el-icon-menu"></i>登录管理<i class="el-icon-arrow-down el-icon--right"></i></span>
			<el-dropdown-menu slot="dropdown">
				<el-dropdown-item command="home">回到首页</el-dropdown-item>
				<el-dropdown-item command="usermanage">用户管理</el-dropdown-item>
				<el-dropdown-item command="signout" divided>退出</el-dropdown-item>
			</el-dropdown-menu>
		</el-dropdown>
    </div>
</template>

<script>
import { signout } from "@/api/getData";
// import { baseImgPath } from "@/config/env";
import { mapActions, mapState } from "vuex";

export default {
  data() {
    return {
      // baseImgPath
    };
  },
  created() {
    if (!this.adminInfo.id) {
      this.getAdminData();
    }
  },
  computed: {
    ...mapState(["adminInfo"])
  },
  methods: {
    ...mapActions(["getAdminData"]),
    async handleCommand(command) {
      if (command == "home") {
        this.$router.push("/manage");
      } else if (command == "signout") {
        const res = await signout();
        if (res.status == 1) {
          this.$message({
            type: "success",
            message: "退出成功"
          });
          this.$router.push("/");
        } else {
          this.$message({
            type: "error",
            message: res.message
          });
        }
      } else if (command == "usermanage") {
        this.$router.push("/adminList");
      }
    }
  }
};
</script>

<style lang="less">
@import "../style/mixin";
.header_container {
  background-color: #eff2f7;
  height: 60px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-left: 20px;
}
// .avator {
//   .wh(36px, 36px);
//   border-radius: 50%;
//   margin-right: 37px;
// }
.el-dropdown-menu__item {
  text-align: center;
}
.el-dropdown-link {
  cursor: pointer;
}
.el-icon-menu {
  padding-right: 10px;
}
</style>
