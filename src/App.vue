<!--
 * @Author: your name
 * @Date: 2020-03-27 01:41:52
 * @LastEditTime: 2020-03-28 02:36:44
 * @LastEditors: Please set LastEditors
 * @Description: In User Settings Edit
 * @FilePath: \xuwentest\src\App.vue
 -->
<template>
  <div id="app">
    <el-container>
      <el-header>装修demo</el-header>

      <el-container>
        <el-aside width="200px">
          <Draggable></Draggable>
        </el-aside>
        <el-main>
          <Layout></Layout>
        </el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import Draggable from "./components/common/draggable";
import Layout from "./components/common/layout";

export default {
  name: "App",
  components: { Draggable,Layout }
};
</script>

<style>
.el-header {
  background-color: #b3c0d1;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
  line-height: 200px;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 160px;
}

body > .el-container {
  margin-bottom: 40px;
}
</style>
