<template>
  <div style="margin-bottom:50px;">
    <el-form ref="form" label-width="80px" :inline="true">
      <el-form-item label="目标星级">
        <el-input v-model="star" style="width: 60px;" type="number"></el-input>
      </el-form-item>

      <el-form-item label="目标张数">
        <el-input v-model="num" style="width: 60px;"></el-input>
      </el-form-item>
    </el-form>

    <el-form ref="form" label-width="80px">
      <el-form-item label="是否绑定">
        <el-radio-group v-model="radio1">
          <el-radio label="1" size="large">是</el-radio>
          <el-radio label="2" size="large">否</el-radio>
        </el-radio-group>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" :icon="EditPen" @click="result=calculate(star,num);analysis=analyze(star,num)">计算
        </el-button>
      </el-form-item>

      <el-form-item label="计算结果">
        <el-input readonly="true" v-model="result" style="width: 150px"></el-input>
      </el-form-item>

      <el-form-item label="结果分析">
        <span readonly="true" v-text="analysis"></span>
      </el-form-item>
    </el-form>

  </div>
  <el-divider></el-divider>

</template>

<script lang="ts" setup>
import { ref } from "vue";
import { EditPen } from "@element-plus/icons-vue";

const star = ref("");
const num = ref("");
const radio1 = ref("");
let result = ref("");
const calculate = (star, num) => {
  if (star > 16 | star < 0 | num < 0) {
    return NaN;
  }
  return String(Math.pow(2, star) * num);
};

let analysis = ref("");
const analyze = (star, num) => {
  if (star > 16) {
    return "卡片星级不能超过16星!";
  }
  if (star < 0) {
    return "卡片星级不能小于0!";
  }
  if (num < 0) {
    return "卡片数量不能小于0!";
  }
  return "经过分析，强化" + num + "张" + star + "星卡牌至少需要" + calculate(star, num) + "张0星卡";
};
</script>

<style scoped>

</style>