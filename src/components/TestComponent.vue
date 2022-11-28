<template>
  <div class="test-component">
    <div class="degree-disaster">
      <h4>灾害程度</h4>
      <div
        id="degree-disaster-echart"
        style="width: 400px; height: 400px"
      ></div>
    </div>
    <div class="degree-type">
      <h4>灾害类型</h4>
      <i class="el-icon-warning"></i>
      <i class="el-icon-s-flag"></i>
      <i class="el-icon-s-opportunity"></i>
    </div>
    <div class="selected-simulation">
      <h4>选中模拟</h4>
      <el-checkbox v-model="allSelect" @change="handleAllChange"
        >全选</el-checkbox
      >
      <el-checkbox-group v-model="checkList" @change="handleSonChange">
        <el-checkbox label="a"></el-checkbox>
        <el-checkbox label="b"></el-checkbox>
        <el-checkbox label="c"></el-checkbox>
      </el-checkbox-group>
    </div>
  </div>
</template>

<script>
import * as echarts from "echarts";
export default {
  name: "TestComponent",
  data() {
    return {
      allSelect: false,
      checkList: [],
    };
  },
  mounted() {
    this.init();
  },
  methods: {
    init() {
      const myChart = echarts.init(
        document.getElementById("degree-disaster-echart")
      );
      const option = {
        tooltip: {
          trigger: "item",
          formatter: "{c0}万亩",
        },
        legend: {
          top: "5%",
          left: "center",
        },
        series: [
          {
            type: "pie",
            radius: ["40%", "70%"],
            avoidLabelOverlap: false,
            label: {
              show: false,
              position: "center",
            },
            emphasis: {
              label: {
                show: true,
                fontSize: "40",
                fontWeight: "bold",
              },
            },
            labelLine: {
              show: false,
            },
            data: [
              { value: 86, name: "受灾" },
              { value: 29, name: "成灾" },
              { value: 15, name: "绝收" },
            ],
          },
        ],
      };
      myChart.setOption(option);
    },
    handleAllChange(val) {
      this.checkList = val ? ["a", "b", "c"] : [];
    },
    handleSonChange(val) {
      this.allSelect = val.length === 3;
    },
  },
};
</script>

<style scoped>
h4 {
  margin: 0 0 20px;
}
.test-component > div {
  margin-bottom: 10px;
  padding: 10px;
  width: 400px;
  border: 2px solid rgb(234, 136, 136);
}
.degree-type i {
  margin-right: 10px;
  font-size: 30px;
  cursor: pointer;
  color: rgb(121, 34, 178);
}
</style>
