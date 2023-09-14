<template>
  <div style="width: 100vw;height: 100vh;overflow: hidden;display: flex">
    <div style="flex: 1">
      <el-image style="width: 100%;height: 100%" fit="cover"
                src="https://img1.baidu.com/it/u=4159158149,2237302473&fm=253&fmt=auto&app=138&f=JPEG?w=800&h=500"></el-image>
    </div>
    <div class="welcome-title">
      <div style="font-size: 30px;font-weight: bold">欢迎来到南孔文化生态系统</div>
      <div style="margin-top: 10px">在这里你可以了解有关南孔文化的一切知识</div>
      <div style="margin-top: 5px">测试使用测试测试</div>
    </div>
    <div style="width: 400px;background-color: white;z-index: 1">
      <router-view v-slot="{ Component }">
        <transition name="el-fade-in-linear" mode="out-in">
          <component :is="Component" style="height: 100%"/>
        </transition>
      </router-view>
    </div>
  </div>


</template>

<script setup>

</script>

<style scoped>
.welcome-title{
  position: absolute;
  bottom: 30px;
  left: 30px;
  color: white;
  text-shadow: 0 0 10px black;
}
</style>