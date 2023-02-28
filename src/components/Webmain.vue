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
          <el-option-group
              :label='"1升2"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover2" class="m-2" placeholder="2升3">
          <el-option-group
              :label='"2升3"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover3" class="m-2" placeholder="3升4">
          <el-option-group
              :label='"3升4"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover4" class="m-2" placeholder="4升5">
          <el-option-group
              :label='"4升5"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover5" class="m-2" placeholder="5升6">
          <el-option-group
              :label='"5升6"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover6" class="m-2" placeholder="6升7">
          <el-option-group
              :label='"6升7"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover7" class="m-2" placeholder="7升8">
          <el-option-group
              :label='"7升8"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover8" class="m-2" placeholder="8升9">
          <el-option-group
              :label='"8升9"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover9" class="m-2" placeholder="9升10">
          <el-option-group
              :label='"9升10"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover10" class="m-2" placeholder="10升11">
          <el-option-group
              :label='"10升11"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover11" class="m-2" placeholder="11升12">
          <el-option-group
              :label='"11升12"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover12" class="m-2" placeholder="12升13">
          <el-option-group
              :label='"12升13"'
          />
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
      </el-form-item>
      <el-form-item label="价值衡量度">
        <el-input-number v-model="star_price" style="width: 100px;" :min="0" :max="13" :step="1" step-strictly/>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" :icon="EditPen" @click="getProgramme()">计算
        </el-button>
      </el-form-item>
      <el-form-item>
        <el-button :icon="MagicStick" type="primary" @click="clearClover()">清空四叶草
        </el-button>
      </el-form-item>
      <br>
      <el-divider><p id="result" style="font-size: 18px;font-weight: bold">计算结果</p></el-divider>
      <br>
      <el-form-item label="上卡方案">
        <span readonly="true" v-html="analysis"></span>
      </el-form-item>
      <el-form-item label="四叶草消耗">
        <span readonly="true" v-html="analysis_clover"></span>
      </el-form-item>
      <el-form-item label="卡片价值">
        <span readonly="true" v-html="analysis_value"></span>
      </el-form-item>
    </el-form>

  </div>
</template>

<script setup>

import {ref} from "vue";
import {EditPen, MagicStick} from "@element-plus/icons-vue";

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

const star_price = ref("");
let analysis = ref(""); //分析
let analysis_clover = ref("");
let analysis_value = ref("");
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
//打开消息提示框
import {ElMessageBox} from 'element-plus'
import {ElNotification} from 'element-plus'

window.onload = function open() {
  ElMessageBox.alert('使用本计算器前请务必查看下方说明', '提醒', {
    confirmButtonText: '确定',
  })
}
//问卷调查
const open2 = () => {
  ElNotification({
    title: '计算完成',
    dangerouslyUseHTMLString: true,
    message: '<strong>如果你有任何问题或建议<br>请参加我们的<a href="https://survey.xiayeqz.com:3999/s/QEFoBL" style="text-decoration: none;color: #409EFF" target="_blank">问卷调查</a></strong>',
    type: 'success',
    duration: 3000,
  })
}

function getProgramme() {
  //验证四叶草输入是否全 -> 这个功能在1.1版本被取消
  // if (clover1.value * clover2.value * clover3.value * clover4.value * clover5.value * clover6.value * clover7.value * clover8.value * clover9.value * clover10.value * clover11.value * clover12.value == 0) {
  //   alert("四叶草输入不全")
  //   return "四叶草输入不全";
  // }


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
  showResult(showProgramme, finalExpection);
}

//结果分析函数
function showResult(showProgramme, finalExpection) {
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  let result = "";
  let k, i;
  for (k = 1; k <= 13; k++) {
    result += "上" + k + "方法：";
    for (i = 0; i <= 2; i++) {
      if (showProgramme[k - 1][i] < 0) {
        result += "X "
      } else {
        result += showProgramme[k - 1][i] + " ";
      }
    }
    result += getCloverbyRate(clover[k - 1]);
    result += " "
    result += "概率：" + ((rateCalculate(k - 1, showProgramme[k - 1][0], showProgramme[k - 1][1], showProgramme[k - 1][2])) * 100).toFixed(0) + "%+" + (bonus.value * rateCalculate(k - 1, showProgramme[k - 1][0], showProgramme[k - 1][1], showProgramme[k - 1][2])).toFixed(2) + "%" + " "
    result += "<br>"
    //result += "期望值：" + finalExpection[k] + '<br>';
  }
  analysis.value = result;
  analysis_clover.value = cloverCalculate(showProgramme); //显示四叶草消耗相关内容
  analysis_value.value = cardValuecalculate(finalExpection); //显示卡片价值相关内容
  //向用户报计算完成
  open2();
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


const rateValid = (rate) => {
  if (rate >= 1) {
    return 1;
  } else {
    return rate;
  }
}

const getCloverbyRate = (rate) => {
  switch (rate) {
    case 1:
      return "不加草";
    case 1.2:
      return "1级四叶草";
    case 1.4:
      return "2级四叶草";
    case 1.7:
      return "3级四叶草";
    case 2.0:
      return "4级四叶草";
    case 2.4:
      return "5级四叶草";
    case 2.7:
      return "6级四叶草";
    case 3.0:
      return "超能四叶草";
    case 3.2:
      return "SS四叶草";
    case 3.6:
      return "SSS四叶草";
    case 4.0:
      return "SSR四叶草";
    default:
      return "未知";
  }
}
//计算一张卡的强化成功率，参数为强化用卡，副卡1，副卡2，副卡3
const rateCalculate = (mainstar, subcard1, subcard2, subcard3) => {
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  var a, b, c;
  if (subcard1 < 0) {
    subcard1 = -1;
  }
  if (subcard2 < 0) {
    subcard2 = -1;
  }
  if (subcard3 < 0) {
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
//本函数仅将计算结果进行拼接显示
const cloverCalculate = (showProgramme) => {
  var result = "";
  var i;
  for (i = 8; i <= 10; i++) {
    var cost1 = cloverCalculate1(i, showProgramme);
    var cost2 = cloverCalculate2(i, showProgramme);
    var cost3 = cloverCalculate3(i, showProgramme);
    var cost4 = cloverCalculate4(i, showProgramme);
    var cost5 = cloverCalculate5(i, showProgramme);
    var cost6 = cloverCalculate6(i, showProgramme);
    var costs = cloverCalculateS(i, showProgramme);
    result += "单张卡上至" + i + "星平均消耗草量<br>"
    if (cost1 == 0 && cost2 == 0 && cost3 == 0 && cost4 == 0 && cost5 == 0 && cost6 == 0 & costs == 0)
      result += "不消耗任何四叶草<br>";
    else {
      if (cost1)
        result += "1级四叶草：" + cost1 + "<br>";
      if (cost2)
        result += "2级四叶草：" + cost2 + "<br>";
      if (cost3)
        result += "3级四叶草：" + cost3 + "<br>";
      if (cost4)
        result += "4级四叶草：" + cost4 + "<br>";
      if (cost5)
        result += "5级四叶草：" + cost5 + "<br>";
      if (cost6)
        result += "6级四叶草：" + cost6 + "<br>";
      if (costs)
        result += "超能四叶草：" + costs + "<br>";
    }
  }
  //用户报计算完成
  return result;
};

const cardValuecalculate = (cost_array) => {
  var result = "";
  var i;
  var star = star_price.value;
  star = Number(star);
  for (i = 10; i <= 13; i++) {
    result += "单张" + i + "平均造价：";
    result += cost_array[i] / cost_array[star];
    result += "张" + star_price.value + "星卡";
    result += "<br>";
  }
  return result;
}

//1级四叶草消耗量计算函数
function cloverCalculate1(star, showProgramme) {
  var k, q;
  var result = 0;
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  if (star <= 1) return 0; //上1不需要任何草，结束递归
  if (star <= 6) {     //计算的等级低于6级时
    if (clover[star - 1] == 1.2) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate1(showProgramme[star - 1][0], showProgramme) + cloverCalculate1(showProgramme[star - 1][1], showProgramme) + cloverCalculate1(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate1(star - 1, showProgramme);
      return result;
    }
    if (clover[star - 1] != 1.2) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate1(showProgramme[star - 1][0], showProgramme) + cloverCalculate1(showProgramme[star - 1][1], showProgramme) + cloverCalculate1(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate1(star - 1, showProgramme);
      return result;
    }
  }
  if (star >= 7) {     //计算的等级大于6级时
    if (clover[star - 1] == 1.2) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate1(showProgramme[star - 1][0], showProgramme) + cloverCalculate1(showProgramme[star - 1][1], showProgramme) + cloverCalculate1(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate1(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate1(star - 1, showProgramme) - cloverCalculate1(star - 2, showProgramme));
      return result;
    }
    if (clover[star - 1] != 1.2) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate1(showProgramme[star - 1][0], showProgramme) + cloverCalculate1(showProgramme[star - 1][1], showProgramme) + cloverCalculate1(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate1(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate1(star - 1, showProgramme) - cloverCalculate1(star - 2, showProgramme));
      return result;
    }
  }
}

//2级四叶草消耗量计算函数
function cloverCalculate2(star, showProgramme) {
  var k, q;
  var result = 0;
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  if (star <= 1) return 0; //上1不需要任何草，结束递归
  if (star <= 6) {     //计算的等级低于6级时
    if (clover[star - 1] == 1.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate2(showProgramme[star - 1][0], showProgramme) + cloverCalculate2(showProgramme[star - 1][1], showProgramme) + cloverCalculate2(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate2(star - 1, showProgramme);
      return result;
    }
    if (clover[star - 1] != 1.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate2(showProgramme[star - 1][0], showProgramme) + cloverCalculate2(showProgramme[star - 1][1], showProgramme) + cloverCalculate2(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate2(star - 1, showProgramme);
      return result;
    }
  }
  if (star >= 7) {     //计算的等级大于6级时
    if (clover[star - 1] == 1.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate2(showProgramme[star - 1][0], showProgramme) + cloverCalculate2(showProgramme[star - 1][1], showProgramme) + cloverCalculate2(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate2(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate2(star - 1, showProgramme) - cloverCalculate2(star - 2, showProgramme));
      return result;
    }
    if (clover[star - 1] != 1.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate2(showProgramme[star - 1][0], showProgramme) + cloverCalculate2(showProgramme[star - 1][1], showProgramme) + cloverCalculate2(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate2(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate2(star - 1, showProgramme) - cloverCalculate2(star - 2, showProgramme));
      return result;
    }
  }
}

//3级四叶草消耗量计算函数
function cloverCalculate3(star, showProgramme) {
  var k, q;
  var result = 0;
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  if (star <= 1) return 0; //上1不需要任何草，结束递归
  if (star <= 6) {     //计算的等级低于6级时
    if (clover[star - 1] == 1.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate3(showProgramme[star - 1][0], showProgramme) + cloverCalculate3(showProgramme[star - 1][1], showProgramme) + cloverCalculate3(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate3(star - 1, showProgramme);
      return result;
    }
    if (clover[star - 1] != 1.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate3(showProgramme[star - 1][0], showProgramme) + cloverCalculate3(showProgramme[star - 1][1], showProgramme) + cloverCalculate3(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate3(star - 1, showProgramme);
      return result;
    }
  }
  if (star >= 7) {     //计算的等级大于6级时
    if (clover[star - 1] == 1.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate3(showProgramme[star - 1][0], showProgramme) + cloverCalculate3(showProgramme[star - 1][1], showProgramme) + cloverCalculate3(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate3(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate3(star - 1, showProgramme) - cloverCalculate3(star - 2, showProgramme));
      return result;
    }
    if (clover[star - 1] != 1.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate3(showProgramme[star - 1][0], showProgramme) + cloverCalculate3(showProgramme[star - 1][1], showProgramme) + cloverCalculate3(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate3(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate3(star - 1, showProgramme) - cloverCalculate3(star - 2, showProgramme));
      return result;
    }
  }
}

//4级四叶草消耗量计算函数
function cloverCalculate4(star, showProgramme) {
  var k, q;
  var result = 0;
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  if (star <= 1) return 0; //上1不需要任何草，结束递归
  if (star <= 6) {     //计算的等级低于6级时
    if (clover[star - 1] == 2.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate4(showProgramme[star - 1][0], showProgramme) + cloverCalculate4(showProgramme[star - 1][1], showProgramme) + cloverCalculate4(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate4(star - 1, showProgramme);
      return result;
    }
    if (clover[star - 1] != 2.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate4(showProgramme[star - 1][0], showProgramme) + cloverCalculate4(showProgramme[star - 1][1], showProgramme) + cloverCalculate4(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate4(star - 1, showProgramme);
      return result;
    }
  }
  if (star >= 7) {     //计算的等级大于6级时
    if (clover[star - 1] == 2.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate4(showProgramme[star - 1][0], showProgramme) + cloverCalculate4(showProgramme[star - 1][1], showProgramme) + cloverCalculate4(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate4(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate4(star - 1, showProgramme) - cloverCalculate4(star - 2, showProgramme));
      return result;
    }
    if (clover[star - 1] != 2.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate4(showProgramme[star - 1][0], showProgramme) + cloverCalculate4(showProgramme[star - 1][1], showProgramme) + cloverCalculate4(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate4(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate4(star - 1, showProgramme) - cloverCalculate4(star - 2, showProgramme));
      return result;
    }
  }
}

//5级四叶草消耗量计算函数
function cloverCalculate5(star, showProgramme) {
  var k, q;
  var result = 0;
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  if (star <= 1) return 0; //上1不需要任何草，结束递归
  if (star <= 6) {     //计算的等级低于6级时
    if (clover[star - 1] == 2.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate5(showProgramme[star - 1][0], showProgramme) + cloverCalculate5(showProgramme[star - 1][1], showProgramme) + cloverCalculate5(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate5(star - 1, showProgramme);
      return result;
    }
    if (clover[star - 1] != 2.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate5(showProgramme[star - 1][0], showProgramme) + cloverCalculate5(showProgramme[star - 1][1], showProgramme) + cloverCalculate5(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate5(star - 1, showProgramme);
      return result;
    }
  }
  if (star >= 7) {     //计算的等级大于6级时
    if (clover[star - 1] == 2.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate5(showProgramme[star - 1][0], showProgramme) + cloverCalculate5(showProgramme[star - 1][1], showProgramme) + cloverCalculate5(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate5(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate5(star - 1, showProgramme) - cloverCalculate5(star - 2, showProgramme));
      return result;
    }
    if (clover[star - 1] != 2.4) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate5(showProgramme[star - 1][0], showProgramme) + cloverCalculate5(showProgramme[star - 1][1], showProgramme) + cloverCalculate5(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate5(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate5(star - 1, showProgramme) - cloverCalculate5(star - 2, showProgramme));
      return result;
    }
  }
}

function cloverCalculate6(star, showProgramme) {
  var k, q;
  var result = 0;
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  if (star <= 1) return 0; //上1不需要任何草，结束递归
  if (star <= 6) {     //计算的等级低于6级时
    if (clover[star - 1] == 2.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate6(showProgramme[star - 1][0], showProgramme) + cloverCalculate6(showProgramme[star - 1][1], showProgramme) + cloverCalculate6(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate6(star - 1, showProgramme);
      return result;
    }
    if (clover[star - 1] != 2.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate6(showProgramme[star - 1][0], showProgramme) + cloverCalculate6(showProgramme[star - 1][1], showProgramme) + cloverCalculate6(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate6(star - 1, showProgramme);
      return result;
    }
  }
  if (star >= 7) {     //计算的等级大于6级时
    if (clover[star - 1] == 2.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculate6(showProgramme[star - 1][0], showProgramme) + cloverCalculate6(showProgramme[star - 1][1], showProgramme) + cloverCalculate6(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate6(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate6(star - 1, showProgramme) - cloverCalculate6(star - 2, showProgramme));
      return result;
    }
    if (clover[star - 1] != 2.7) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculate6(showProgramme[star - 1][0], showProgramme) + cloverCalculate6(showProgramme[star - 1][1], showProgramme) + cloverCalculate6(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculate6(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculate6(star - 1, showProgramme) - cloverCalculate6(star - 2, showProgramme));
      return result;
    }
  }
}

function cloverCalculateS(star, showProgramme) {
  var k, q;
  var result = 0;
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1];
  if (star <= 1) return 0; //上1不需要任何草，结束递归
  if (star <= 6) {     //计算的等级低于6级时
    if (clover[star - 1] == 3.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculateS(showProgramme[star - 1][0], showProgramme) + cloverCalculateS(showProgramme[star - 1][1], showProgramme) + cloverCalculateS(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculateS(star - 1, showProgramme);
      return result;
    }
    if (clover[star - 1] != 3.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculateS(showProgramme[star - 1][0], showProgramme) + cloverCalculateS(showProgramme[star - 1][1], showProgramme) + cloverCalculateS(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculateS(star - 1, showProgramme);
      return result;
    }
  }
  if (star >= 7) {     //计算的等级大于6级时
    if (clover[star - 1] == 3.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q;
      result += 1 / q * (cloverCalculateS(showProgramme[star - 1][0], showProgramme) + cloverCalculateS(showProgramme[star - 1][1], showProgramme) + cloverCalculateS(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculateS(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculateS(star - 1, showProgramme) - cloverCalculateS(star - 2, showProgramme));
      return result;
    }
    if (clover[star - 1] != 3.0) {
      k = (1 + 0.01 * bonus.value) * rateCalculate(star - 1, showProgramme[star - 1][0], showProgramme[star - 1][1], showProgramme[star - 1][2]);
      q = rateValid(k);
      result += 1 / q * (cloverCalculateS(showProgramme[star - 1][0], showProgramme) + cloverCalculateS(showProgramme[star - 1][1], showProgramme) + cloverCalculateS(showProgramme[star - 1][2], showProgramme));
      result += cloverCalculateS(star - 1, showProgramme);
      result += ((1 / q) - 1) * (cloverCalculateS(star - 1, showProgramme) - cloverCalculateS(star - 2, showProgramme));
      return result;
    }
  }
}
</script>

<style scoped>
.form {
  font-family: 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB',
  'Microsoft YaHei', '微软雅黑', Arial, sans-serif;
}
</style>
