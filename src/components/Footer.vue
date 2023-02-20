<script setup>
import {useDark} from '@vueuse/core'

const isDark = useDark()


</script>
<template>
  <el-form ref="form" label-width="100px" :inline="true">
    <el-form-item label="深色模式">
      <el-switch size="laige" v-model="isDark"/>

    </el-form-item>
  </el-form>
  <h5>说明:</h5>
  <span class="notice">1.计算结果为通过计算机模拟大量样本情况下的最终结果，其中宝石和点券消耗取整数，四叶草消耗取两位小数<br>2.若宝石初始星低于10，程序会计算将宝石强化到10星的材料消耗；若宝石星级大于等于10，程序会计算将宝石强化到15星的材料消耗<br>3.成功率加成为打开背包后鼠标移动到“属性加成”区域显示的“卡片成功率+ xx%”字样。本程序认为游戏中给出的概率表示实际上为相加关系，例如“80%+20%”会作为100%处理<br> 如果你任何有疑问或建议，欢迎参加我们的<a
      href="https://survey.xiayeqz.com:3999/s/QEFoBL" target="_blank" style="color: #409EFF">问卷调查</a></span>
  <el-divider></el-divider>
  <h5>贡献者:</h5>
  <a href="https://github.com/czyczy608" target="_blank">
    <el-tooltip content="czyczy608" placement="top">
      <el-avatar
          src="https://avatars.githubusercontent.com/u/57560140?v=4">
      </el-avatar>

    </el-tooltip>
    &ensp;</a>
  <a href="https://github.com/Xiaye2332" target="_blank">
    <el-tooltip content="Xiaye2332" placement="top">
      <el-avatar
          src="https://avatars.githubusercontent.com/u/86192453?v=4">
      </el-avatar>
    </el-tooltip>
    &ensp;</a>
  <a href="https://github.com/superboyyy" target="_blank">
    <el-tooltip content="superboyyy" placement="top">
      <el-avatar
          src="https://avatars.githubusercontent.com/u/75305545?v=4">
      </el-avatar>
    </el-tooltip>
  </a>
  <span class="notice"><br><br>本页面遵照GPLv3协议开放源代码，您可以自由传播和修改，转载请注明作者和出处<br><a
      href="https://github.com/Xiaye2332/FVM_Calculator" target="_blank"><img
      src="https://img.shields.io/badge/Github-FVM_Calculator%20v1.3-purple"></a></span>
  <el-divider></el-divider>
  <h5>更新日志:</h5>
  <span class="notice">2023/1/26 &nbsp;正式立项<br>2023/2/19 &nbsp;测试版发布<br><br></span>
</template>

<style scoped>


*, :before, :after {
  box-sizing: border-box;
}


img {
  max-width: 100%;
}

.page-content .doc-content a {
  display: inline-flex;
  align-items: center;
}


a {
  font-weight: 500;
  text-decoration: inherit;
}

a, area, button, [role=button], input, label, select, summary, textarea {
  touch-action: manipulation;
}

body {
  margin: 0;
  width: 100%;
  min-width: 320px;
  min-height: 100vh;
  line-height: 1.4;
  font-size: 16px;
  font-weight: 400;
  direction: ltr;
  font-synthesis: none;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  transition: background-color var(--el-transition-duration-fast);
}

body {
  font-family: Helvetica Neue, Helvetica, PingFang SC, Hiragino Sans GB, Microsoft YaHei, \5fae\8f6f\96c5\9ed1, Arial, sans-serif;
  font-weight: 400;
  font-size: var(--el-font-size-base);
  color: var(--el-text-color-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-tap-highlight-color: transparent;
}


.notice {
  font-family: Helvetica Neue, Helvetica, PingFang SC, Hiragino Sans GB, Microsoft YaHei, \5fae\8f6f\96c5\9ed1, Arial, sans-serif;
  font-weight: 400;
  font-size: var(--el-font-size-base);
  color: var(--el-text-color-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-tap-highlight-color: transparent;
  margin-bottom: 50px;
}


</style>
