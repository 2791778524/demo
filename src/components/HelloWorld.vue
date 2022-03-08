<template>
  <div>
    <div id="main1" style="width: 300px; height: 400px"></div>
    <div id="main2" style="width: 300px; height: 400px"></div>
    <div id="main3" style="width: 300px; height: 400px"></div>
    <button @click="stopTimer">关闭</button>
    <button @click="goTimer">开始</button>
  </div>
</template>

<script>
import * as echarts from "echarts";
export default {
  name: "HelloWorld",
  data() {
    timer: null
  },
  methods: {
    getEchart1() {
      let myChart = echarts.init(document.getElementById("main1"));
      myChart.setOption({
        xAxis: {
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        yAxis: {},
        series: [
          {
            type: "bar",
            data: [23, 24, 18, 25, 27, 28, 25],
            barWidth: "20%",
            itemStyle: {
              color: "red",
              borderColor: "pink",
              borderWidth: 1,
              opacity: 0.5,
              shadowColor: "#91cc75",
              shadowBlur: 3,
            },
          },
          {
            type: "bar",
            data: [26, 24, 18, 22, 23, 20, 27],
          },
          {
            type: "bar",
            data: [26, 24, 18, 22, 23, 20, 27],
          },
        ],
      });
    },
    getEchart2() {
      let myChart = echarts.init(document.getElementById("main2"));
      let option = {
        xAxis: {
          data: ["A", "B", "C", "D", "E"],
        },
        yAxis: {},
        series: [
          {
            data: [10, 22, 28, 43, 49],
            type: "bar",
            stack: "y",
          },
          {
            data: [10, 22, 28, 43, 49],
            type: "bar",
            stack: "x",
          },
          {
            data: [5, 4, 3, 5, 10],
            type: "bar",
            stack: "y",
          },
          {
            data: [5, 4, 3, 5, 10],
            type: "bar",
            stack: "x",
          },
        ],
      };
      myChart.setOption(option);
    },
    getEchart3() {
      let myChart = echarts.init(document.getElementById('main3'))
      let data = [];
      for (let i = 0; i < 5; i++) {
        data.push(Math.round(Math.random() * 200));
      }
      let option = {
        xAxis: {
          max: "dataMax",
        },
        yAxis: {
          type: "category",
          data: ["A", "B", "C", "D", "E"],
          inverse: true,
          animationDuration: 300,
          animationDurationUpdate: 300,
          max: 2, // only the largest 3 bars will be displayed
        },
        series: [
          {
            realtimeSort: true,
            name: "销售额",
            type: "bar",
            data: data,
            label: {
              show: true,
              position: "right",
              valueAnimation: true,
            },
          },
        ],
        legend: {
          show: true,
        },
        animationDuration: 3000,
        animationDurationUpdate: 3000,
        animationEasing: "linear",
        animationEasingUpdate: "linear",
      };
      function updata() {
        let data = option.series[0].data;
        for (let i = 0; i < data.length; ++i) {
          if (Math.random() > 0.9) {
            data[i] += Math.round(Math.random() * 2000);
          } else {
            data[i] += Math.round(Math.random() * 200);
          }
        }
        myChart.setOption(option)
      }
      this.timer = setInterval(()=>{
        updata()
      },1000)
    },
    stopTimer() {
      clearInterval(this.timer)
    },
    goTimer() {
      this.getEchart3()
    }
  },
  mounted() {
    this.getEchart1();
    this.getEchart2();
    this.getEchart3();
  },
};
</script>

<style scoped>
</style>
