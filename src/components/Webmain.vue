<template>
  <div style="margin-bottom:50px;" class="form">
    <el-form ref="form" label-width="100px" :inline="true">
      <!--      <el-form-item label="目标星级">-->
      <!--        <el-input v-model="star" style="width: 100px;" type="number"-->
      <!--                  oninput="this.value = this.value.replace(/[^0-9]/g, '');">-->
      <!--        </el-input>-->
      <!--      </el-form-item>-->


    </el-form>

    <el-form ref="form" label-width="100px">
      <el-form-item label="成功率加成">
        <el-input v-model="bonus" style="width: 100px;" oninput="this.value = this.value.replace(/[^0-9]/g, '');">
          <template #append>%</template>
        </el-input>
      </el-form-item>
      <el-form-item label="四叶草选择">
        <el-select v-model="clover1" class="m-2" placeholder="1升2">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover2" class="m-2" placeholder="2升3">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover3" class="m-2" placeholder="3升4">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover4" class="m-2" placeholder="4升5">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover5" class="m-2" placeholder="5升6">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover6" class="m-2" placeholder="6升7">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover7" class="m-2" placeholder="7升8">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover8" class="m-2" placeholder="8升9">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover9" class="m-2" placeholder="9升10">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover10" class="m-2" placeholder="10升11">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover11" class="m-2" placeholder="11升12">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover12" class="m-2" placeholder="12升13">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
      </el-form-item>
      <!--      <el-form-item label="是否绑定">-->
      <!--        <el-radio-group v-model="radio1">-->
      <!--          <el-radio label="1" size="large">是</el-radio>-->
      <!--          <el-radio label="2" size="large">否</el-radio>-->
      <!--        </el-radio-group>-->
      <!--      </el-form-item>-->

      <el-form-item>
        <el-button type="primary" :icon="EditPen" @click="getProgramme()">计算
        </el-button>
      </el-form-item>



      <el-form-item label="计算结果">
        <span readonly="true" v-html="analysis"></span>
      </el-form-item>
    </el-form>

  </div>
</template>

<script lang="ts" setup>
import {ref} from "vue";
import {EditPen} from "@element-plus/icons-vue";

//const star = ref("");  //星级变量
//const num = ref("");   //卡牌数变量
const bonus = ref("");  //成功率加成变量
const clover1 = ref(""); //定义四叶草变量
const clover2 = ref("");
const clover3 = ref("");
const clover4 = ref("");
const clover5 = ref("");
const clover6 = ref("");
const clover7 = ref("");
const clover8 = ref("");
const clover9 = ref("");
const clover10 = ref("");
const clover11 = ref("");
const clover12 = ref("");

// const radio1 = ref("");

let analysis = ref(""); //分析
//定义四叶草标签名和实际值，value即为cloverx.value直接引出值
const options = [
  {
    value: 1.0,
    label: '不加草',
  },
  {
    value: 1.2,
    label: '1级四叶草',
  },
  {
    value: 1.4,
    label: '2级四叶草',
  },
  {
    value: 1.7,
    label: '3级四叶草',
  },
  {
    value: 2.0,
    label: '4级四叶草',
  },
  {
    value: 2.4,
    label: '5级四叶草',
  },
  {
    value: 2.7,
    label: '6级四叶草',
  },
  {
    value: 3.0,
    label: '超能四叶草',
  },
  {
    value: 3.2,
    label: 'SS四叶草',
  },
  {
    value: 3.6,
    label: 'SSS四叶草',
  },
  {
    value: 4,
    label: 'SSR四叶草',
  },
]
//定义概率表，主卡为0-12星
const rate = [
  [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
  [0.88, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
  [0.608, 0.792, 0.968, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
  [0, 0.429, 0.55, 0.686, 0.88, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
  [0, 0, 0.242, 0.403, 0.495, 0.88, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
  [0, 0, 0, 0.201, 0.33, 0.396, 0.88, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1],
  [0, 0, 0, 0, 0.132, 0.264, 0.319, 0.88, 1, 1, 1, 1, 1, 1, 1, 1, 1],
  [0, 0, 0, 0, 0, 0.106, 0.212, 0.264, 0.88, 1, 1, 1, 1, 1, 1, 1, 1],
  [0, 0, 0, 0, 0, 0, 0.06, 0.132, 0.22, 0.88, 1, 1, 1, 1, 1, 1, 1],
  [0, 0, 0, 0, 0, 0, 0, 0.022, 0.045, 0.135, 0.88, 1, 1, 1, 1, 1, 1],
  [0, 0, 0, 0, 0, 0, 0, 0, 0.018, 0.046, 0.125, 0.88, 1, 1, 1, 1, 1, 1],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0.017, 0.043, 0.116, 0.88, 1, 1, 1, 1],
  [0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0.0157, 0.0398, 0.107, 0.88, 1, 1, 1]
]

const programme = [  //19种方案表，0表示同星级，-1表示低1星，-2表示低2星，-30表示不放卡，后续函数会将负数星级处理为不放卡
  [0, -30, -30],
  [-1, -30, -30],
  [-2, -30, -30],
  [0, 0, -30],
  [0, -1, -30],
  [0, -2, -30],
  [-1, -1, -30],
  [-1, -2, -30],
  [-2, -2, -30],
  [0, 0, 0],
  [0, 0, -1],
  [0, 0, -2],
  [0, -1, -1],
  [0, -1, -2],
  [0, -2, -2],
  [-1, -1, -1],
  [-1, -1, -2],
  [-1, -2, -2],
  [-2, -2, -2]
]

var finalExpection = new Array();//存储各个星级卡的期望价值，函数每次重新执行的时候需要初始化
var finalProgramme = new Array();//存储最终使用的方案，开始前也需要初始化
var showProgramme = new Array();

function getProgramme() {
  //验证四叶草输入是否全
  if (clover1.value * clover2.value * clover3.value * clover4.value * clover5.value * clover6.value * clover7.value * clover8.value * clover9.value * clover10.value * clover11.value * clover12.value == 0) {
    alert("四叶草输入不全")
    return "四叶草输入不全";
  }

  //初始化期望值，0星卡为1，其余初始化为-1，方便后续操作
  //初始化方案，全为-1
  let i = 0;
  while (i <= 13) {
    finalExpection[i] = -1;
    finalProgramme[i] = -1;
    showProgramme[i] = new Array();
    i++;
  }
  finalExpection[0] = 1;
  //初始化完成

  let mainStar = 0;
  while (mainStar < 13) {//主卡从0到12星
    let numProgramme = 0;//方案序号，从0~18
    while (numProgramme < 19) {
      let nowExpection = getExpection(mainStar, mainStar + programme[numProgramme][0], mainStar + programme[numProgramme][1], mainStar + programme[numProgramme][2]);
      //alert(mainStar+"\n"+mainStar+programme[numProgramme][0]+","+mainStar+programme[numProgramme][1]+","+mainStar+programme[numProgramme][2]+"\n"+nowExpection);
      if (nowExpection > 0 && (finalExpection[mainStar + 1] == -1 || finalExpection[mainStar + 1] > nowExpection)) {//如果当前方案可行并且得出的下一星期望更优，则替换下一星期望和最优方案
        finalExpection[mainStar + 1] = nowExpection;//替换下一星期望
        finalProgramme[mainStar] = numProgramme;//替换最优方案
      }
      numProgramme++;
    }
    mainStar++;
  }
  //到此为止，完成各个方案的计算

  i = 0;
  while (i < 13) {
    showProgramme[i][0] = i + programme[finalProgramme[i]][0];
    showProgramme[i][1] = i + programme[finalProgramme[i]][1];
    showProgramme[i][2] = i + programme[finalProgramme[i]][2];
    i++;
  }


  //alert(showProgramme);
  //alert(finalExpection);
  showResult(showProgramme,finalExpection);
}
function showResult(showProgramme,finalExpection) {
  let result = "";
  let k,i;
  for (k = 1; k <= 13; k++) {
    result += "上" + k + "方法：";
    for (i=0;i<=2;i++){
      if(showProgramme[k-1][i] < 0){
        result += "X "
      }else{
        result += showProgramme[k-1][i] + " ";
      }
    }
    result += "概率："+((rateCalculate(k-1,showProgramme[k-1][0],showProgramme[k-1][1],showProgramme[k-1][2]))*100).toFixed(0)+"%+"+(bonus.value*rateCalculate(k-1,showProgramme[k-1][0],showProgramme[k-1][1],showProgramme[k-1][2])).toFixed(2)+"%"+" "
    result += "期望值："+finalExpection[k]+ '<br>';
    }
  analysis.value=result;
}

function getExpection(mainStar, subStar1, subStar2, subStar3) {
  if (subStar1 < 0) {
    return -1;
  }//无法放卡，直接令该方案无效

  if (subStar2 < 0) {
    subStar2 = -1;
  }
  if (subStar3 < 0) {
    subStar3 = -1;
  }//预处理好星级

  let nowRate = rateCalculate(mainStar, subStar1, subStar2, subStar3);//计算该方案下的概率
  nowRate = rateValid(nowRate * (1 + 0.01 * bonus.value));
  let inputValue = finalExpection[subStar1];
  if (subStar2 >= 0) {
    inputValue += finalExpection[subStar2];
  }
  if (subStar3 >= 0) {
    inputValue += finalExpection[subStar3];
  }//计算I

  let expection;
  if (mainStar < 6) {//此时强化不掉级
    expection = finalExpection[mainStar] + inputValue / nowRate;
    return expection;
  } else {//强化掉级
    expection = (finalExpection[mainStar] + inputValue - (1 - nowRate) * finalExpection[mainStar - 1]) / nowRate;
    return expection;
  }
}


// const calculate = (star, num) => {  //废弃的函数
//   if (star > 16 | star <= 0 | num <= 0) {
//     return NaN;
//   }
//   return rateCalculate(star,star,-1,-1);
// };
//


const rateValid = (rate) => {
  if (rate >= 1) {
    return 1;
  } else {
    return rate;
  }
}


//计算一张卡的强化成功率，参数为强化用卡，副卡1，副卡2，副卡3
const rateCalculate = (mainstar, subcard1, subcard2, subcard3) => {
  //将用户输入的四叶草数值存储到数组中
  var clover = [1, clover1.value, clover2.value, clover3.value, clover4.value, clover5.value, clover6.value, clover7.value, clover8.value, clover9.value, clover10.value, clover11.value, clover12.value];
  var a, b, c;
  if (subcard1 < 0){
    subcard1 = -1;
  }
  if (subcard2 < 0){
    subcard2 = -1;
  }
  if (subcard3 < 0){
    subcard3 = -1;
  }
  if (clover[mainstar] == 0) {
    return "四叶草传入缺少"
  }
  if (mainstar < 0 | mainstar > 12 | subcard1 > 16 | subcard2 > 16 | subcard3 > 16) {
    return "传入的星级不合法";
  }
  if (subcard1 == -1) {
    return "副卡1不能为-1";
  }
  if (subcard2 == -1 && subcard3 == -1) {
    a = rate[mainstar][subcard1];
    b = 0;
    c = 0;
    return rateValid(a * clover[mainstar]);
  }
  if (subcard2 != -1 && subcard3 == -1) {
    a = rate[mainstar][subcard1];
    b = rate[mainstar][subcard2];
    c = 0;
    return rateValid((a + b / 3) * clover[mainstar]);
  }
  if (subcard2 == -1 && subcard3 != -1) {
    a = rate[mainstar][subcard1];
    b = 0;
    c = rate[mainstar][subcard3];
    return rateValid((a + c / 3) * clover[mainstar]);
  }
  if (subcard2 != -1 && subcard3 != -1) {
    a = rate[mainstar][subcard1];
    b = rate[mainstar][subcard2];
    c = rate[mainstar][subcard3];
  }
  return rateValid((a + b / 3 + c / 3) * clover[mainstar]);
};


// const analyze = (star, num) => { //废弃的分析函数
//   if (star > 16) {
//     return "卡片星级不能超过16星";
//   }
//   if (star <= 0) {
//     return "卡片星级必须为正数";
//   }
//   if (num <= 0) {
//     return "卡片数量必须为正数";
//   }
//   return "经过分析，成功率为"+rateCalculate(star,star-1,-1,-1);
// };


</script>

<style scoped>
.form {
  font-family: 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB',
  'Microsoft YaHei', '微软雅黑', Arial, sans-serif;
}
</style>