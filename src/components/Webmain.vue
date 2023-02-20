<template>
  <div class="form" style="margin-bottom:50px;">

    <el-form ref="form" :inline="true" label-width="100px">
      <!--      <el-form-item label="目标星级">-->
      <!--        <el-input v-model="star" style="width: 100px;" type="number"-->
      <!--                  oninput="this.value = this.value.replace(/[^0-9]/g, '');">-->
      <!--        </el-input>-->
      <!--      </el-form-item>-->


    </el-form>

    <el-form ref="form" label-width="100px">
      <el-form-item label="宝石初始星">
        <el-input v-model="initialstar" oninput="this.value = this.value.replace(/[^0-9]/g, '');" style="width: 100px;">
          <template #append>星</template>
        </el-input>
      </el-form-item>
      <el-form-item label="成功率加成">
        <el-input v-model="bonus" oninput="this.value = this.value.replace(/[^0-9]/g, '');" style="width: 100px;">
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
        <el-select v-model="clover13" class="m-2" placeholder="13升14">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
        <el-select v-model="clover14" class="m-2" placeholder="14升15">
          <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value"
          />
        </el-select>
      </el-form-item>
      <el-form-item label="保险金选择">
        <el-checkbox v-model="insurance6" label="上7" size="large"/>
        <el-checkbox v-model="insurance7" label="上8" size="large"/>
        <el-checkbox v-model="insurance8" label="上9" size="large"/>
        <el-checkbox v-model="insurance9" label="上10" size="large"/>
        <el-checkbox v-model="insurance10" label="上11" size="large"/>
        <el-checkbox v-model="insurance11" label="上12" size="large"/>
        <el-checkbox v-model="insurance12" label="上13" size="large"/>
        <el-checkbox v-model="insurance13" label="上14" size="large"/>
        <el-checkbox v-model="insurance14" label="上15" size="large"/>
      </el-form-item>

      <el-form-item>
        <el-button :icon="EditPen" type="primary" @click="Calculate()">计算
        </el-button>
      </el-form-item>
      <br>
      <el-divider><p id="result" style="font-size: 18px;font-weight: bold">计算结果</p></el-divider>
      <br>

      <el-form-item label="水晶消耗量">
        <img style="visibility: hidden" src="src/assets/imgs/transparent.png">
        <img style="visibility: hidden;position: absolute" id="normal" src="src/assets/imgs/0x12700010.png">
        <span readonly="true" v-html="normalcost"></span>
        <img style="visibility: hidden;position: absolute" id="abnormal" src="src/assets/imgs/0x12700120.png">
        <span readonly="true" v-html="abnormalcost"></span>
      </el-form-item>

      <el-form-item label="四叶草消耗">
        <span readonly="true" id="noconsume" style="visibility: hidden;position: absolute">不消耗任何四叶草</span>
        <img style="visibility: hidden" id="S" src="src/assets/imgs/S.png">
        <span readonly="true" v-html="scost"></span>
        <img style="visibility: hidden" id="SS" src="src/assets/imgs/SS.png">
        <span readonly="true" v-html="sscost"></span>
        <img style="visibility: hidden" id="SSS" src="src/assets/imgs/SSS.png">
        <span readonly="true" v-html="ssscost"></span>
        <img style="visibility: hidden" id="SSR" src="src/assets/imgs/SSR.png">
        <span readonly="true" v-html="ssrcost"></span>
      </el-form-item>

      <el-form-item label="点券消耗量">
        <span readonly="true" v-html="pointcost"></span>
        <img id="D" style="visibility: hidden" src="src/assets/imgs/D.png">
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
const initialstar = ref("0");  //宝石初始星级
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
const clover13 = ref("");
const clover14 = ref("");
const insurance6 = ref(false)
const insurance7 = ref(false)
const insurance8 = ref(false)
const insurance9 = ref(false)
const insurance10 = ref(false)
const insurance11 = ref(true)
const insurance12 = ref(true)
const insurance13 = ref(true)
const insurance14 = ref(true)
const normalcost = ref("")
const abnormalcost = ref("")
const pointcost = ref("")
const scost = ref("")
const sscost = ref("")
const ssscost = ref("")
const ssrcost = ref("")


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
//定义概率表，宝石主卡为0-15rate[0]-rate[14]
const rate = [1, 0.88, 0.75, 0.63, 0.5, 0.38, 0.26, 0.19, 0.13, 0.10, 0.09, 0.08, 0.07, 0.06, 0.05]

//定义宝石消耗表
const crystalcost = [5, 10, 15, 25, 35, 55, 75, 100, 130, 160, 200, 245, 300, 355, 420]
const insurancecost = [0, 0, 0, 0, 0, 0, 400, 500, 600, 2500, 3000, 3500, 4000, 4500, 5000]


//打开消息提示框
import {ElMessageBox} from 'element-plus'
import {ElNotification} from 'element-plus'

window.onload = function open() {
  ElMessageBox.alert('使用本计算器前请务必查看下方说明', '提醒', {
    confirmButtonText: '确定',
  })
}
//问卷调查
const success = () => {
  ElNotification({
    title: '计算完成',
    dangerouslyUseHTMLString: true,
    message: '当前为测试版本，如遇任何问题请直接提出',
    type: 'success',
    duration: 3000,
  })
}
const exeception = (text) => {
  ElNotification({
    title: '计算出错',
    dangerouslyUseHTMLString: true,
    message: text,
    type: 'error',
    duration: 3000,
  })
}

const rateValid = (rate) => {
  if (rate >= 1) {
    return 1;
  } else {
    return rate;
  }
}

//入口函数
function Calculate() {
  //判断条件
  if (initialstar.value >= 15) {
    exeception("宝石初始星级不合法");
    initialstar.value = "";
    return;
  }
  if (initialstar.value == "") {
    initialstar.value = "0";
  }
  //是否使用保险金的Boolean数组
  var insurance = [false, false, false, false, false, false, insurance6.value, insurance7.value, insurance8.value, insurance9.value, insurance10.value, insurance11.value, insurance12.value, insurance13.value, insurance14.value];
  //点券计算部分
  var star;
  var totalpoint = 0;
  var flag = (initialstar.value >= 10) ? 14 : 9;
  for (star = initialstar.value; star <= flag; star++) {
    if (!insurance[star]) continue;
    totalpoint += (1 / rateCalculate(star) * insurancecost[star]);
  }
  //水晶计算部分
  var abnormal = abnormalCrystalCalculate(initialstar.value * 1, 14, insurance);
  var normal = normalCrystalCalculate(initialstar.value * 1, 9, insurance);
  //四叶草计算部分
  var clovers = cloverCalculateS(initialstar.value, flag, insurance);
  var cloverss = cloverCalculateSS(initialstar.value, flag, insurance);
  var cloversss = cloverCalculateSSS(initialstar.value, flag, insurance);
  var cloverssr = cloverCalculateSSR(initialstar.value, flag, insurance);
  ShowResult(totalpoint, normal, abnormal, clovers, cloverss, cloversss, cloverssr);


}

function ShowResult(d, normal, abnormal, clovers, cloverss, cloversss, cloverssr) {
  if (initialstar.value >= 10) {
    document.getElementById("abnormal").style.visibility = "visible";
    abnormalcost.value = "x" + String(Math.round(abnormal));
    document.getElementById("normal").style.visibility = "hidden";
    normalcost.value = "";
    document.getElementById("result").innerHTML = "从<img id='initialstar'</img>上<img src='/src/assets/imgs/15.png'</img>需要"
    document.getElementById("initialstar").src = '/src/assets/imgs/' + initialstar.value + '.png'
  } else {
    document.getElementById("normal").style.visibility = "visible";
    normalcost.value = "x" + String(Math.round(normal));
    document.getElementById("abnormal").style.visibility = "hidden";
    abnormalcost.value = "";
    document.getElementById("result").innerHTML = "从<img id='initialstar'</img>上<img src='/src/assets/imgs/10.png'</img>需要"
    document.getElementById("initialstar").src = '/src/assets/imgs/' + initialstar.value + '.png'
  }
  if (clovers || cloverss || cloversss || cloverssr) {
    document.getElementById("noconsume").style.visibility = "hidden";
    document.getElementById("S").style.visibility = "visible";
    document.getElementById("SS").style.visibility = "visible";
    document.getElementById("SSS").style.visibility = "visible";
    document.getElementById("SSR").style.visibility = "visible";
    scost.value = "<br>x" + String(Math.floor(clovers * 100) / 100);
    sscost.value = "<br>x" + String(Math.floor(cloverss * 100) / 100);
    ssscost.value = "<br>x" + String(Math.floor(cloversss * 100) / 100);
    ssrcost.value = "<br>x" + String(Math.floor(cloverssr * 100) / 100);
  }
  else {
    document.getElementById("noconsume").style.visibility = "visible";
    document.getElementById("S").style.visibility = "hidden";
    document.getElementById("SS").style.visibility = "hidden";
    document.getElementById("SSS").style.visibility = "hidden";
    document.getElementById("SSR").style.visibility = "hidden";
    scost.value = "";
    sscost.value = "";
    ssscost.value = "";
    ssrcost.value = "";
  }

  if (d) {
    pointcost.value = String(Math.round(d));
    document.getElementById("D").style.visibility = "visible";
  } else {
    pointcost.value = "0";
    document.getElementById("D").style.visibility = "visible";
  }
  success()
}

function rateCalculate(mainstar) {
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1, (clover13.value > 0) ? clover13.value : 1, (clover14.value > 0) ? clover14.value : 1];
  return (rateValid((1.0 + 1.0 * bonus.value / 100) * rate[mainstar] * clover[mainstar]));
}


function normalCrystalCalculate(initialstar, mainstar, insurance) {
  var cost = 0;
  if (mainstar < initialstar) return 0;//需要计算的星级小于预定的初始星，直接返回0
  if (mainstar < 0) return 0;//上0截止
  if (mainstar >= 6 && mainstar < 10) {
    if (insurance[mainstar] == true) {
      cost += normalCrystalCalculate(initialstar, mainstar - 1, insurance);
      cost += crystalcost[mainstar] * 1 / rateCalculate(mainstar);
    }
    if (insurance[mainstar] == false) {
      cost += crystalcost[mainstar] * 1 / rateCalculate(mainstar);
      cost += normalCrystalCalculate(initialstar, mainstar - 1, insurance);
      cost += (1 / rateCalculate(mainstar) - 1) * (normalCrystalCalculate(initialstar, mainstar - 1, insurance) - normalCrystalCalculate(initialstar, mainstar - 2, insurance));
    }
  }
  if (mainstar <= 5) {
    cost += 1 / rateCalculate(mainstar) * crystalcost[mainstar];
    cost += normalCrystalCalculate(initialstar, mainstar - 1, insurance);
  }
  return cost;
}

function abnormalCrystalCalculate(initialstar, mainstar, insurance) {

  var cost = 0;
  if (mainstar < initialstar) return 0;//需要计算的星级小于预定的初始星，直接返回0
  if (mainstar < 10) return 0;//上10截止
  if (insurance[mainstar] == true) {
    cost += abnormalCrystalCalculate(initialstar, mainstar - 1, insurance);
    cost += crystalcost[mainstar] * 1 / rateCalculate(mainstar);
  }
  if (insurance[mainstar] == false) {
    cost += crystalcost[mainstar] * 1 / rateCalculate(mainstar);
    cost += abnormalCrystalCalculate(initialstar, mainstar - 1, insurance);
    cost += (1 / rateCalculate(mainstar) - 1) * (abnormalCrystalCalculate(initialstar, mainstar - 1, insurance) - abnormalCrystalCalculate(initialstar, mainstar - 2, insurance));
  }
  return cost;
}

//S草计算函数
function cloverCalculateS(initialstar, mainstar, insurance) {
  var cost = 0;
  if (mainstar < initialstar) return 0;//需要计算的星级小于预定的初始星，直接返回0
  if (mainstar < 0) return 0;//上0截止
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1, (clover13.value > 0) ? clover13.value : 1, (clover14.value > 0) ? clover14.value : 1];
  if (clover[mainstar] == 3.0) {
    if (mainstar >= 6) {
      if (insurance[mainstar] == true) {
        cost += cloverCalculateS(initialstar, mainstar - 1, insurance);
        cost += 1 / rateCalculate(mainstar);
      }
      if (insurance[mainstar] == false) {
        cost += 1 / rateCalculate(mainstar);
        cost += cloverCalculateS(initialstar, mainstar - 1, insurance);
        cost += (1 / rateCalculate(mainstar) - 1) * (cloverCalculateS(initialstar, mainstar - 1, insurance) - cloverCalculateS(initialstar, mainstar - 2, insurance));
      }
    }
    if (mainstar <= 5) {
      cost += 1 / rateCalculate(mainstar);
      cost += cloverCalculateS(initialstar, mainstar - 1, insurance);
    }
  } else return cloverCalculateS(initialstar, mainstar - 1, insurance);
  return cost;
}

//SS草计算函数
function cloverCalculateSS(initialstar, mainstar, insurance) {
  var cost = 0;
  if (mainstar < initialstar) return 0;//需要计算的星级小于预定的初始星，直接返回0
  if (mainstar < 0) return 0;//上0截止
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1, (clover13.value > 0) ? clover13.value : 1, (clover14.value > 0) ? clover14.value : 1];
  if (clover[mainstar] == 3.2) {
    if (mainstar >= 6) {
      if (insurance[mainstar] == true) {
        cost += cloverCalculateSS(initialstar, mainstar - 1, insurance);
        cost += 1 / rateCalculate(mainstar);
      }
      if (insurance[mainstar] == false) {
        cost += 1 / rateCalculate(mainstar);
        cost += cloverCalculateSS(initialstar, mainstar - 1, insurance);
        cost += (1 / rateCalculate(mainstar) - 1) * (cloverCalculateSS(initialstar, mainstar - 1, insurance) - cloverCalculateSS(initialstar, mainstar - 2, insurance));
      }
    }
    if (mainstar <= 5) {
      cost += 1 / rateCalculate(mainstar);
      cost += cloverCalculateSS(initialstar, mainstar - 1, insurance);
    }
  } else return cloverCalculateSS(initialstar, mainstar - 1, insurance);
  return cost;
}


//SSS草计算函数
function cloverCalculateSSS(initialstar, mainstar, insurance) {
  var cost = 0;
  if (mainstar < initialstar) return 0;//需要计算的星级小于预定的初始星，直接返回0
  if (mainstar < 0) return 0;//上0截止
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1, (clover13.value > 0) ? clover13.value : 1, (clover14.value > 0) ? clover14.value : 1];
  if (clover[mainstar] == 3.6) {
    if (mainstar >= 6) {
      if (insurance[mainstar] == true) {
        cost += cloverCalculateSSS(initialstar, mainstar - 1, insurance);
        cost += 1 / rateCalculate(mainstar);
      }
      if (insurance[mainstar] == false) {
        cost += 1 / rateCalculate(mainstar);
        cost += cloverCalculateSSS(initialstar, mainstar - 1, insurance);
        cost += (1 / rateCalculate(mainstar) - 1) * (cloverCalculateSSS(initialstar, mainstar - 1, insurance) - cloverCalculateSSS(initialstar, mainstar - 2, insurance));
      }
    }
    if (mainstar <= 5) {
      cost += 1 / rateCalculate(mainstar);
      cost += cloverCalculateSSS(initialstar, mainstar - 1, insurance);
    }
  } else return cloverCalculateSSS(initialstar, mainstar - 1, insurance);
  return cost;
}

//SSR草计算函数
function cloverCalculateSSR(initialstar, mainstar, insurance) {
  var cost = 0;
  if (mainstar < initialstar) return 0;//需要计算的星级小于预定的初始星，直接返回0
  if (mainstar < 0) return 0;//上0截止
  //将用户输入的四叶草数值存储到数组中,这里自动排除不填的问题，当作不加草判断
  var clover = [1, (clover1.value > 0) ? clover1.value : 1, (clover2.value > 0) ? clover2.value : 1, (clover3.value > 0) ? clover3.value : 1, (clover4.value > 0) ? clover4.value : 1, (clover5.value > 0) ? clover5.value : 1, (clover6.value > 0) ? clover6.value : 1, (clover7.value > 0) ? clover7.value : 1, (clover8.value > 0) ? clover8.value : 1, (clover9.value > 0) ? clover9.value : 1, (clover10.value > 0) ? clover10.value : 1, (clover11.value > 0) ? clover11.value : 1, (clover12.value > 0) ? clover12.value : 1, (clover13.value > 0) ? clover13.value : 1, (clover14.value > 0) ? clover14.value : 1];
  if (clover[mainstar] == 4.0) {
    if (mainstar >= 6) {
      if (insurance[mainstar] == true) {
        cost += cloverCalculateSSR(initialstar, mainstar - 1, insurance);
        cost += 1 / rateCalculate(mainstar);
      }
      if (insurance[mainstar] == false) {
        cost += 1 / rateCalculate(mainstar);
        cost += cloverCalculateSSR(initialstar, mainstar - 1, insurance);
        cost += (1 / rateCalculate(mainstar) - 1) * (cloverCalculateSSR(initialstar, mainstar - 1, insurance) - cloverCalculateSSR(initialstar, mainstar - 2, insurance));
      }
    }
    if (mainstar <= 5) {
      cost += 1 / rateCalculate(mainstar);
      cost += cloverCalculateSSR(initialstar, mainstar - 1, insurance);
    }
  } else return cloverCalculateSSR(initialstar, mainstar - 1, insurance);
  return cost;
}

</script>

<style scoped>
.form {
  font-family: 'Helvetica Neue', Helvetica, 'PingFang SC', 'Hiragino Sans GB',
  'Microsoft YaHei', '微软雅黑', Arial, sans-serif;
}
</style>
