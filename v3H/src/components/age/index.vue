<template>
  <div class="box2">
    <div class="title">
      <p>年龄比例</p>
      <img src="@/assets/image/screen_title_tag.png" />
    </div>
    <div class="echat" ref="charts"></div>
  </div>
</template>
<script lang="ts" setup>
import { ref, onMounted } from "vue";
import * as echarts from "echarts";
let charts = ref();
onMounted(() => {
  let myChart = echarts.init(charts.value);
  myChart.setOption({
    tooltip: {
      // 鼠标悬停显示卡片
      trigger: "item",
    },
    legend: {
      top: "12%",
      left: "60%",
      itemGap: 16,
      itemStyle: {
        borderWidth: 2,
      },
      textStyle: {
        color: "#fff",
        padding: [0, 0, 0, 10],
      },
    },
    series: [
      {
        name: "年龄比例",
        type: "pie",
        radius: ["45%", "80%"],
        itemStyle: {
          borderRadius: 10,
          borderColor: "#fff",
          borderWidth: 4,
          fontSize: 24,
        },
        label: {
          show: true,
          position: "center",
          formatter: "本日总数",
          color: "rgba(255,255,255,.5)",
          fontSize: 14,
        },
        data: [
          { value: 16, name: "10岁以下 16%" },
          { value: 8, name: "10-18岁 8%" },
          { value: 12, name: "18-30岁 12%" },
          { value: 24, name: "30-40岁 24%" },
          { value: 20, name: "40-60岁 20%" },
          { value: 20, name: "60岁以上 20%" },
        ],
        right: 160,
        top: 10,
      },
    ],
  });
});
</script>

<style lang="scss" scoped>
.box2 {
  width: 100%;
  height: 100%;
  background: url(@/assets/image/screen_main_IB.png) no-repeat;
  background-size: 100% 100%;
  margin-top: 3px;
  margin-left: 15px;
  .title {
    color: white;
    font-size: 20px;
    transform: translate(38px);
  }
  .echat {
    width: 495px;
    height: 240px;
  }
}
</style>