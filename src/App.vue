<script setup>

import {onMounted, ref} from "vue";
import {v4 as uuidv4} from 'uuid';
import axios from "axios";
import {ElMessage} from "element-plus";

const viewType = ref('1')
const viewOptions = [
  {
    label: '控制页',
    value: '1'
  },
  {
    label: '历史页',
    value: '2'
  }
]

function changeView(val) {
  if (val === '2') {
    // 获取所有历史记录
    // TODO: 加上url
    axios.get(`/web/queryRoundHistory`)
        .then(res => {
          // TODO: 把这里的代码取消注释
          // historyControlList.value = res.data.data
        })
        .catch(err => {
          console.log(err)
        })
  }
}

onMounted(() => {
  document.body.style.setProperty('--el-color-primary', '#5C0686');
})

const controlParams ={
  projectId: 148,
  date: "2024-06-25",
  hour: '01:00',
  controlModel: 2,
  model: 0,
  roundId: '',
  isConfirmExecute: true,
  deviceNumConfirm: {
    date: "2024-06-25",
    hour: "01:00",
    roundId: "",
    deviceMode: 2,
    sgkNum: 3,//
    sgkLqtNum: 2,//
    sgkLqbNum: 2,//
    yecbNum: 1,//
    ycLdbNum: 1,//
    sgkLdbDeltaTemp: 5,//
    sgkLdbDeltaPre: 0.5,//
    jzNum: 2,//
    jzLqtNum: 2,//
    jzLqbNum: 2,//
    jzLdbNum: 2,//
    jzLdbDeltaTemp: 4.5,//
    jzLdbDeltaPre: 0.4,//
    sgkOutTemp: 7,//
    sgkLqtBjd: 1.5,//
    sgkLqsDeltaTemp: 6,//
    yecbDeltaTemp: 3,//
    bcOutTemp: 8,//
    jzOutTemp: 6.5,//
    jzLqtBjd: 1.2,//
    jzLqsDeltaTemp: 5.5,//
    lzOutTemp: 9,//
    lzDeltaPre: 0.6,//
    lzDeltaTemp: 4,//
    tygLdbNum: 1,
    yygLdbNum: 1,
    eastSyLdbNum: 1,
    westSyLdbNum: 1,
    tygKtxNum: 2,
    dtKtxNum: 2,
    tygLdbDeltaTemp: 3.5,
    yygLdbDeltaTemp: 3.5,
    eastSyLdbDeltaTemp: 3.5,
    westSyLdbDeltaTemp: 3.5,
    tygKtTemp: 22,
    dtKtTemp: 23
  }
}

const controlParamsList = [
    // 台数 0-8
  {key: 'sgkNum', label: '双工况冷机台数', type: 'number', value: 3, min: 0, max: 4, editable: true},
  {key: 'sgkLqtNum', label: '双工况冷却塔台数', type: 'number', value: 2, min: 0, max: 4, editable: true},
  {key: 'sgkLqbNum', label: '双工况冷却泵台数', type: 'number', value: 2, min: 0, max: 4, editable: true},
  {key: 'yecbNum', label: '乙二醇泵台数', type: 'number', value: 1, min: 0, max: 4, editable: true},
  {key: 'ycLdbNum', label: '一次冷冻泵台数', type: 'number', value: 1, min: 0, max: 4, editable: true},
  {key: 'jzNum', label: '基载冷机台数', type: 'number', value: 0, min: 0, max: 4, editable: true},
  {key: 'jzLqtNum', label: '基载冷却塔台数', type: 'number', value: 0, min: 0, max: 4, editable: true},
  {key: 'jzLqbNum', label: '基载冷却泵台数', type: 'number', value: 0, min: 0, max: 4, editable: true},
  {key: 'jzLdbNum', label: '基载冷冻泵台数', type: 'number', value: 0, min: 0, max: 4, editable: true},

    // 冷站系统设定参数 9-24
  {key: 'sgkOutTemp', label: '双工况冷机出水温度', type: 'number', value: 7, editable: true},
  {key: 'sgkLqtBjd', label: '双工况冷却塔逼近度', type: 'number', value: 1.5, editable: true},
  {key: 'sgkLqsDeltaTemp', label: '双工况冷却水供回水温差', type: 'number', value: 6, editable: true},
  {key: 'sgkLdbDeltaTemp', label: '双工况冷冻泵供回水温差', type: 'number', value: 5, editable: true},
  {key: 'sgkLdbDeltaPre', label: '双工况冷冻泵供回水压差', type: 'number', value: 0.5, editable: true},
  {key: 'yecbDeltaTemp', label: '乙二醇泵供回水温差', type: 'number', value: 3, editable: true},
  {key: 'bcOutTemp', label: '冰槽出水温度', type: 'number', value: 8, editable: false},
  {key: 'jzOutTemp', label: '基载冷机出水温度', type: 'number', value: 6.5, editable: true},
  {key: 'jzLqtBjd', label: '基载冷却塔逼近度', type: 'number', value: 1.2, editable: true},
  {key: 'jzLqsDeltaTemp', label: '基载冷却水供回水温差', type: 'number', value: 5.5, editable: true},
  {key: 'jzLdbDeltaTemp', label: '基载冷冻泵供回水温差', type: 'number', value: 4.5, editable: true},
  {key: 'jzLdbDeltaPre', label: '基载冷冻泵供回水压差', type: 'number', value: 0.4, editable: true},
  {key: 'lzOutTemp', label: '冷站供水温度', type: 'number', value: 9, editable: false},
  {key: 'lzDeltaPre', label: '冷站供回水压差', type: 'number', value: 0.6, editable: false},
  {key: 'lzDeltaTemp', label: '冷站供回水温差', type: 'number', value: 4, editable: false},

    // 换热站水泵及空调箱开启台数
  {key: 'tygLdbNum', label: '体育馆冷冻水泵台数', type: 'number', value: 1, editable: true},
  {key: 'yygLdbNum', label: '游泳馆冷冻水泵台数', type: 'number', value: 1, editable: true},
  {key: 'eastSyLdbNum', label: '东侧商业冷冻水泵台数', type: 'number', value: 1, editable: true},
  {key: 'westSyLdbNum', label: '西侧商业冷冻水泵台数', type: 'number', value: 1, editable: true},
  {key: 'tygKtxNum', label: '体育馆空调箱台数', type: 'number', value: 2, editable: true},
  {key: 'dtKtxNum', label: '大厅空调箱台数', type: 'number', value: 2, editable: true},
  {key: 'tygLdbDeltaTemp', label: '体育馆冷冻水泵供回水温差', type: 'number', value: 3.5, editable: true},
  {key: 'yygLdbDeltaTemp', label: '游泳馆冷冻水泵供回水温差', type: 'number', value: 3.5, editable: true},
  {key: 'eastSyLdbDeltaTemp', label: '东侧商业冷冻水泵供回水温差', type: 'number', value: 3.5, editable: true},
  {key: 'westSyLdbDeltaTemp', label: '西侧商业冷冻水泵供回水温差', type: 'number', value: 3.5, editable: true},
  {key: 'tygKtTemp', label: '体育馆空调箱温度', type: 'number', value: 22, editable: false},
  {key: 'dtKtTemp', label: '大厅空调箱温度', type: 'number', value: 23, editable: false},
]

const params = ref({
  ...controlParams.deviceNumConfirm
})

const runMode = ref('1')
const runModeOptions = [
  {
    label: '无操作',
    value: '0'
  },
  {
    label: '制冰模式',
    value: '1'
  },
  {
    label: '制冰、基载供冷',
    value: '2'
  },
  {
    label: '制冰+余温供冷+基载供冷',
    value: '3'
  },
  {
    label: '单融冰供冷',
    value: '4'
  },
  {
    label: '融冰+冷机联合供冷',
    value: '5'
  },
  {
    label: '冷机直供',
    value: '6'
  }
]

async function submitScheme() {
  const now = new Date()
  const yyyy = now.getFullYear()
  const mm = String(now.getMonth() + 1).padStart(2, '0')
  const dd = String(now.getDate()).padStart(2, '0')
  // 时间
  params.value.date = `${yyyy}-${mm}-${dd}`
  params.value.hour = `${now.getHours().toString().padStart(2, '0')}:00`

  // 初始化uuid
  let uuid = uuidv4()
  params.value.roundId = uuid

  // 判断是否执行任何以及存在任务后采用同样uuid的逻辑
  try {
    // TODO: 添加url
    const res = await axios.get(`/web/queryRoundInfoByDate`, {
      params: {
        date: params.value.date,
        hour: params.value.hour
      }
    })

    const data = res.data.data

    if (data.executionStatus === null && data.endTime === null) {
      ElMessage({
        message: '当前正在执行任务，请稍后提交',
        type: 'warning'
      })
      return null
    } else if (data.executionStatus === 1) {
      ElMessage({
        message: '本小时指令已经成功，请下一小时再执行',
        type: 'warning'
      })
      return null
    }

    if (data.roundId !== '' && data.roundId !== null) {
      uuid = data.roundId
    }

  } catch (error) {
    console.error('请求失败:', error)
    return null
  }

  params.value.deviceMode = Number(runMode.value)

  const scheme = {
    projectId: 148,
    date: params.value.date,
    hour: params.value.hour,
    controlModel: 2,
    model: params.value.deviceMode,
    roundId: uuid,
    isConfirmExecute: true,
    deviceNumConfirm: params.value
  }

  // TODO: 需要添加url
  axios.post(`/web/taskStartNoAlgo`, scheme)
      .then(res => {
        if (res.data.success) {
          ElMessage({
            message: res.data.message,
            type: 'success'
          })
        }
      })
      .catch(err => {
        ElMessage({
          message: err.message,
          type: 'error'
        })
      })
}

// 历史页
const historyControlList = ref([
  {
    roundId: "ca0d3b17-0db8-4f11-9121-25607f09620c",
    date: "2025-05-19",
    hour: "14:00"
  }
])

const isShowHistoryDetail = ref(false)

function closeHistoryDialog() {
  isShowHistoryDetail.value = false
}

const activeRound = ref('1')
const roundDetail = ref([
  // {
  //   "date": "2025-05-19",
  //   "hour": "14:00",
  //   "roundId": "ca0d3b17-0db8-4f11-9121-25607f09620c",
  //   "rounds": 1,
  //   "isRepeat": 0,
  //   "roundStatus": 1,
  //   "roundStartTime": "2025-06-23 00:57:16",
  //   "roundEndTime": "2025-06-23 00:10:11",
  //   "deviceList": [
  //     {
  //       "deviceId": 4099,
  //       "deviceName": "冷却塔01#-02#\nLQT1",
  //       "paramId": 7552,
  //       "paramName": "出水温度",
  //       "beforeParamValue": "27.50",
  //       "executeParamValue": "23.03",
  //       "executeParamName": null,
  //       "executeStartTime": "2025-06-23 00:18:04",
  //       "executeEndTime": "2025-06-23 00:18:04",
  //       "executeStatus": 3,
  //       "postCheckPassed": 2
  //     }
  //   ]
  // },
])

async function checkHistoryDetail(id) {
  // TODO: 需要取消这段的注释，然后给每个请求加上url
  // try {
  //   const res = await axios.get('/web/queryRoundsByRoundId', {
  //     params: { roundId: id }
  //   })
  //
  //   const roundsList = res.data.data.map(item => item.rounds)
  //
  //   const requestList = roundsList.map(rounds =>
  //       axios.get('/web/queryRoundStatus', {
  //         params: { roundId: id, rounds: rounds }
  //       }).then(res => res.data.data)
  //   )
  //
  //   roundDetail.value = await Promise.all(requestList)
  //   isShowHistoryDetail.value = true
  // } catch (error) {
  //   console.error('请求失败：', error)
  // }
}

const statusMap = {
  1: '成功',
  2: '失败',
  3: '无需执行'
}
</script>

<template>
  <div class="flex flex-col w-full h-full">
    <div class="top-container flex flex-row justify-between p-[20px] text-[24px] text-primary font-bold border-b-[1px] border-solid border-[#E5E5E5]">
      <div class="flex flex-row gap-[20px] items-center">
        <img src="/Logo.svg" alt="logo" class="w-[30px] h-[30px]"/>
        <div>杭州奥体中心智能BA控制系统</div>
      </div>
      <div class="custom-segmented">
        <el-segmented style="width: 300px" v-model="viewType" :options="viewOptions" @change="changeView"/>
      </div>
    </div>

<!--    控制页-->
    <div v-if="viewType === '1'" class="flex flex-col gap-[20px] p-[20px]">
      <div class="flex flex-row items-center gap-[10px]">
        <div class="font-bold">运行模式</div>
        <div class="custom-segmented">
          <el-segmented style="width: 1200px" v-model="runMode" :options="runModeOptions" />
        </div>
      </div>
      <div class="grid grid-cols-3 gap-[30px] h-[600px]">
        <div class="flex flex-col gap-[10px] pr-[10px]">
          <div class="text-primary font-bold text-[20px]">冷站设备开启台数设定</div>
          <div v-for="item in controlParamsList.slice(0, 9)" :key="item.key" class="param-item grid grid-cols-2 gap-[10px] items-center">
            <label>{{ item.label }}</label>
            <input v-model="params[item.key]" type="number" :min="item.min" :max="item.max" :disabled="!item.editable" />
          </div>
        </div>

        <div class="flex flex-col gap-[10px] pr-[10px]">
          <div class="text-primary font-bold text-[20px]">冷站运行参数设定</div>
          <div v-for="item in controlParamsList.slice(9, 24)" :key="item.key" class="param-item grid grid-cols-2 gap-[10px] items-center">
            <label>{{ item.label }}</label>
            <input v-model="params[item.key]" type="number" :min="item.min" :max="item.max" :disabled="!item.editable"/>
          </div>
        </div>

        <div class="flex flex-col gap-[10px] pr-[10px]">
          <div class="text-primary font-bold text-[20px]">冷站运行参数设定</div>
          <div v-for="item in controlParamsList.slice(24, 36)" :key="item.key" class="param-item grid grid-cols-2 gap-[10px] items-center">
            <label>{{ item.label }}</label>
            <input v-model="params[item.key]" type="number" :min="item.min" :max="item.max" :disabled="!item.editable" />
          </div>
        </div>
      </div>
    </div>

<!--    历史页-->
    <div v-if="viewType === '2'" class="flex flex-col flex-1  p-[20px]">
      <div class="p-[10px] grid grid-cols-6 font-bold bg-[#E5E5E5] border-b-[1px] border-solid border-[#E5E5E5] rounded-t-[8px]">
        <div class="col-span-2">轮次ID</div>
        <div>日期</div>
        <div>时间</div>
        <div class="col-span-2">
          操作
        </div>
      </div>
      <div class="flex flex-col gap-[10px] overflow-y-auto">
        <div v-for="h in historyControlList" :key="h.roundId" class="p-[10px] grid grid-cols-6 border-b-[1px] border-solid border-[#E5E5E5]">
          <div class="col-span-2">{{h.roundId}}</div>
          <div>{{h.date}}</div>
          <div>{{h.hour}}</div>
          <div class="col-span-2 flex flex-row">
            <div class="underline text-primary cursor-pointer" @click="checkHistoryDetail(h.roundId)">
              详情
            </div>
          </div>
        </div>
      </div>

    </div>

    <div v-if="viewType === '1'" class="w-full flex flex-row p-[20px]">
      <div class="ml-auto gap-[20px] flex flex-row">
        <button class="primary-button cursor-pointer" @click="submitScheme">提交</button>
        <button class="text-black cursor-pointer">重置参数</button>
      </div>
    </div>

  </div>

  <el-dialog
      :model-value="isShowHistoryDetail"
      width="80%"
      align-center
      :show-close=false
      style="background-color: var(--bg-color); border-radius: 12px;"
      @close="closeHistoryDialog"
  >
    <template #header>
        <div class="text-primary font-bold text-[20px] p-[10px]">执行轮次和记录</div>
    </template>
    <div class="p-[10px]">
      <el-tabs v-model="activeRound" class="tabs">
        <el-tab-pane
            v-for="r in roundDetail"
            :key="r.roundId"
            :label="`轮次-${r.rounds}`"
            :name="`${r.rounds}`"
        >
         <div class="flex flex-col gap-[10px] h-[600px]">
           <div class="font-bold grid grid-cols-12 gap-[10px] text-black mb-[10px]">
             <div class="col-span-2">设备名</div>
             <div class="col-span-2">参数名</div>
             <div class="col-span-2">开始执行时间</div>
             <div class="col-span-2">结束执行时间</div>
             <div>调整前参数值</div>
             <div>调整后参数值</div>
             <div>执行的参数名</div>
             <div>执行结果</div>
           </div>
           <div class="overflow-y-auto flex flex-col gap-[10px]">
             <div v-for="d in r.deviceList" :key="d.deviceId" class="grid grid-cols-12 gap-[10px]">
               <div class="col-span-2">{{d.deviceName}}</div>
               <div class="col-span-2">{{d.paramName}}</div>
               <div class="col-span-2">{{d.executeStartTime}}</div>
               <div class="col-span-2">{{d.executeEndTime}}</div>
               <div>{{d.beforeParamValue}}</div>
               <div>{{d.executeParamValue}}</div>
               <div>{{d.executeParamName}}</div>
               <div>{{statusMap[d.executeStatus] || '未知'}}</div>
             </div>
           </div>
         </div>
        </el-tab-pane>
      </el-tabs>
    </div>
  </el-dialog>
</template>

<style scoped>
.custom-segmented .el-segmented {
  --el-segmented-item-selected-color: white;
  --el-segmented-item-selected-bg-color: var(--primary-color);
  --el-border-radius-base: 16px;
}

input {
  border: 1px solid var(--border-color);
  border-radius: 6px;
  padding: 8px;
  outline: none;
  width: 100%;
  box-sizing: border-box;
  font-size: 14px;
  color: var(--text-color);
  background-color: var(--bg-color);
  transition: all 0.2s ease-in-out;
  height: 30px;
}

input:focus {
  border-color: var(--primary-color);
}

input::placeholder {
  color: var(--text-secondary-color);
}

input:disabled {
  background-color: #f0f0f0; /* 灰色背景 */
  color: #999999;            /* 字体变淡 */
  border-color: #dcdcdc;     /* 可选：边框也变淡 */
  cursor: not-allowed;       /* 鼠标变成禁用状态 */
}

.primary-button {
  padding: 6px 16px;
  border-radius: 8px;
  transition: all 0.2s ease-in-out;
  background-color: var(--primary-color);
  color: white;
  width: 100px;
}

.primary-button:hover {
  background-color: var(--primary-color);
  box-shadow: 0 0 10px 1px #5C0686FF, 0 0 20px #7a19a8;
}
</style>
