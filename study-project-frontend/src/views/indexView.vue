<template>
  <div>
    欢迎{{store.auth.user.username}}进入南孔文化生态系统
  </div>
  <div>
    <el-button @click="logout" type="danger" plain>退出登录</el-button>
  </div>
</template>

<script setup>
import {ElMessage} from "element-plus";
import router from "@/router";
import {get} from "@/net";
import {useStore} from "@/stores";

const store = useStore()
const logout = () => {
  get('/api/auth/logout',(message) => {
    const successMessage = message || "退出成功";
    ElMessage.success(successMessage)
    store.auth.user = null
    router.push('/')
  })
}
</script>



<style scoped>

</style>