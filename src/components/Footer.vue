<template>

  <h5>说明:</h5>
  <span class="notice">1.成功率加成为打开背包后鼠标移动到“属性加成”区域显示的“卡片成功率+ xx%”字样。本程序认为游戏中给出的概率表示实际上为相加关系。例如“80%+20%”会作为100%处理 <br> 2.计算结果为通过计算机模拟大量样本情况下的最终结果 <br> 3.期望值表示按照目前给出的强化方案，强化到各个星级所需要的0星好卡的平均数量。建议用户通过不断调整四叶草使用方案，来观察期望值的变化，从而挑选出较为适合自身的强化方案</span>
  <el-divider></el-divider>
  <h5>贡献者:</h5>
  <div class="mb-4" data-v-732d6162="">
    <div class="flex flex-wrap gap-4 pt-2" data-v-732d6162="">
      <div style="height:32px;vertical-align: center;display: inline"><a class="link-item link flex gap-2 items-center link" href="https://github.com/superboyyy"
                                 style="text-decoration: none;color:black" target="_blank"><img
        src="https://avatars.githubusercontent.com/u/75305545?v=4" class="w-8 h-8 rounded-full"> <span>skydyboy</span>
        <!----></a></div>

      <br><br>

      <div style="height:32px;"><a class="link-item link flex gap-2 items-center link" href="https://github.com/Xiaye2332"
                                 style="text-decoration: none;color:black" target="_blank"><img
        src="https://avatars.githubusercontent.com/u/86192453?v=4" class="w-8 h-8 rounded-full"> <span style="margin:auto">夏夜浅酌</span>
        <!----></a></div>

      <br>

      <div style="height:32px;"><a class="link-item link flex gap-2 items-center link" href="https://space.bilibili.com/59516411"
                                   style="text-decoration: none;color:black" target="_blank"><img
          src="http://mms0.baidu.com/it/u=891284316,1073249366&fm=253&app=138&f=JPEG&fmt=auto&q=75?w=300&h=300" class="w-8 h-8 rounded-full"> <span style="margin:auto">剑舞青芒</span>
        <!----></a></div>
    </div>
  </div>
  <span class="notice">本页面遵照GPLv3协议开放源代码，您可以自由传播和修改，转载请注明作者和出处<br></span>
  <el-divider></el-divider>
  <h5>更新日志:</h5>
  <span class="notice">2023/1/4 取消了四叶草不全的提示，现不填写则默认不加四叶草；在结果区域展示所用四叶草<br><br><br></span>
</template>

<style scoped>

.mb-4 {
  margin-bottom: 1rem;
}
*, :before, :after {
  box-sizing: border-box;
}
.rounded-full {
  border-radius: 9999px;
}
.w-8 {
  width: 2rem;
}
.h-8 {
  height: 2rem;
}
img {
  max-width: 100%;
}
.page-content .doc-content a {
  display: inline-flex;
  align-items: center;
}
.gap-2 {
  grid-gap: 0.5rem;
  gap: 0.5rem;
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
  font-family: Helvetica Neue,Helvetica,PingFang SC,Hiragino Sans GB,Microsoft YaHei,\5fae\8f6f\96c5\9ed1,Arial,sans-serif;
  font-weight: 400;
  font-size: var(--el-font-size-base);
  color: var(--el-text-color-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-tap-highlight-color: transparent;
}
.link-item[data-v-36735cb0] {
  display: flex;
  align-items: center;
}
.notice {
  font-family: Helvetica Neue,Helvetica,PingFang SC,Hiragino Sans GB,Microsoft YaHei,\5fae\8f6f\96c5\9ed1,Arial,sans-serif;
  font-weight: 400;
  font-size: var(--el-font-size-base);
  color: var(--el-text-color-primary);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  -webkit-tap-highlight-color: transparent;
  margin-bottom: 50px;
}
</style>