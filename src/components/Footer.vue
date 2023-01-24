<script setup>
import { useDark } from '@vueuse/core'

const isDark = useDark()


</script>
<template>
  <el-form ref="form" label-width="100px" :inline="true">
    <el-form-item label="深色模式">
      <el-switch size="laige" v-model="isDark"/>

    </el-form-item>
  </el-form>
  <h5>说明:</h5>
  <span class="notice">1.计算结果为通过计算机模拟大量样本情况下的最终结果<br>2.四叶草消耗仅统计单张卡从0上到7、8、9三个星级需要消耗的1至5级四叶草总量，目的是便于大批量业制卡时控制四叶草成本<br>3.成功率加成为打开背包后鼠标移动到“属性加成”区域显示的“卡片成功率+ xx%”字样。本程序认为游戏中给出的概率表示实际上为相加关系。例如“80%+20%”会作为100%处理 <br> 4.期望值表示按照目前给出的强化方案，强化到各个星级所需要的0星好卡的平均数量。建议用户通过不断调整四叶草使用方案，来观察期望值的变化，从而挑选出较为适合自身的强化方案<br><br>如果你任何有疑问或建议，欢迎参加我们的<a
      href="https://survey.xiayeqz.com:3999/s/QEFoBL" target="_blank" style="color: #409EFF">问卷调查</a></span>
  <el-divider></el-divider>
  <h5>贡献者:</h5>
  <el-tooltip content="czyczy608" placement="top">
    <el-avatar :size="50">
      <a target="_blank" href="https://github.com/czyczy608"><img
          src="https://avatars.githubusercontent.com/u/57560140?v=4"
      />
      </a>
    </el-avatar>
  </el-tooltip>
  &ensp;
  <el-tooltip content="Xiaye2332" placement="top">
    <el-avatar :size="50">
      <a target="_blank" href="https://github.com/Xiaye2332"><img
          src="https://avatars.githubusercontent.com/u/86192453?v=4"
      />
      </a>
    </el-avatar>
  </el-tooltip>
  &ensp;
  <el-tooltip content="superboyyy" placement="top">
    <el-avatar :size="50">
      <a target="_blank" href="https://github.com/superboyyy"><img
          src="https://avatars.githubusercontent.com/u/75305545?v=4"
      />
      </a>
    </el-avatar>
  </el-tooltip>
  <span class="notice"><br><br>本页面遵照GPLv3协议开放源代码，您可以自由传播和修改，转载请注明作者和出处<br><a
      href="https://github.com/Xiaye2332/FVM_Calculator" target="_blank"><img
      src="https://img.shields.io/badge/Github-FVM_Calculator%20v1.2-blue"></a></span>
  <el-divider></el-divider>
  <h5>更新日志:</h5>
  <span class="notice">2023/1/4 &ensp; 取消了四叶草不全的提示，现不填写则默认不加四叶草；在结果区域展示所用四叶草<br>2023/1/22 &nbsp;更改了部分说明；新增查看强化单张7、8、9星卡的四叶草消耗的选项(仅显示1、2、3、4、5草消耗量)<br>2023/1/25 &nbsp;更改了贡献者区域的前端显示框架，新增“深色模式”滑块<br><br><br></span>
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
