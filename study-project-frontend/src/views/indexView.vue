<template>
  <div>
    欢迎进入南孔文化生态系统
  </div>
  <div>
    <el-button @click="logout" type="danger" plain>退出登录</el-button>
  </div>
</template>

<script setup>
import {ElMessage} from "element-plus";
import router from "@/router";
import {get} from "@/net";

const logout = () => {
  get('/api/auth/logout',(message) => {
    const successMessage = message || "退出成功";
    ElMessage.success(successMessage)
    router.push('/')
  })
}
</script>



<style scoped>

</style>