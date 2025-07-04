
<template>
  <div class="common-layout">
    <el-container>
      <el-header> <el-button type="success" @click="handleClick">Hello Element Plus</el-button></el-header>
      <el-main>  <el-button type="primary" @click="greet">Greet</el-button>
        <p>{{ greetMsg }}</p></el-main>
    </el-container>
  </div>
</template>
<script setup lang="ts">
import { ref } from "vue";
import { invoke } from "@tauri-apps/api/core";
import { ElMessage } from "element-plus";

const greetMsg = ref("");
const name = ref("");
const handleClick = () => {
  ElMessage.success("버튼이 클릭되었습니다!");
}
``
async function greet() {
  // Learn more about Tauri commands at https://tauri.app/develop/calling-rust/
  greetMsg.value = await invoke("greet", { name: name.value });
}
</script>
<style lang="css" scoped>
.common-layout {
  height: 100%;
  width: 100%;
}
.el-header {
  background-color: #f5f5f5;
  text-align: center;
  padding: 10px;
}
.el-main {
  padding: 20px;
  background-color: #ffffff;
}
.el-button {
  margin: 10px;
}
</style>

