<template>
  <el-container style="height: 570px; border: 1px solid #eee">
    <el-aside width="200px" >
      <el-menu :unique-opened="true" :default-active="$route.path"            @select="handleSelect">
        <el-submenu index="1">
          <template slot="title"><i class="el-icon-message"></i>问题管理</template>
          <el-menu-item index="questionListOfUser">问题列表</el-menu-item>
          <el-menu-item index="blockedQuestionListOfUser">屏蔽问题列表</el-menu-item>
        </el-submenu>
        <el-submenu index="2">
          <template slot="title"><i class="el-icon-menu"></i>回答管理</template>
          <el-menu-item index="answerList">回答列表</el-menu-item>
          <el-menu-item index="blockedAnswerList">屏蔽回答列表</el-menu-item>
        </el-submenu>
        <el-submenu index="3">
          <template slot="title"><i class="el-icon-setting"></i>评论管理</template>
          <el-menu-item index="commentList">评论列表</el-menu-item>
          <el-menu-item index="blockedCommentList">屏蔽评论列表</el-menu-item>
      </el-submenu>
        <el-menu-item index="personalInformationOfUser"><i class="el-icon-setting"></i>个人信息</el-menu-item>
      </el-menu>
    </el-aside>
      <el-main style="background-color: #fbfdf8">

        <router-view></router-view>
      </el-main>



  </el-container>

</template>

<script>
  export default {
    name: "userGuide",
    data() {
      const item = {
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      };
      return {
        tableData: Array(20).fill(item)
      }
    },
    methods:{
      handleSelect(path){
        this.$router.push(path)
      },
    }
  };
</script>

<style>

  .el-aside {
    color: #333;
  }
</style>
