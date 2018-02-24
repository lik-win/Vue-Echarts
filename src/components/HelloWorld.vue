<template>
  <div class="hello">
    <div id="myECharts"></div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data() {
    return {
    }
  },
  mounted() {
    this.drawLine();
  },
  methods: {
    drawLine() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById('myECharts'))
      var data = [];

      for (var i = 0; i <= 100; i++) {
        var theta = i / 100 * 360;
        var r = 5 * (1 + Math.sin(theta / 180 * Math.PI));
        data.push([r, theta]);
      }
      // 绘制图表
      myChart.setOption({
        title: {
          text: '极坐标双数值轴'
        },
        legend: {
          data: ['line']
        },
        polar: {},
        tooltip: {
          trigger: 'axis',
          axisPointer: {
            type: 'cross'
          }
        },
        angleAxis: {
          type: 'value',
          startAngle: 0
        },
        radiusAxis: {
        },
        series: [{
          coordinateSystem: 'polar',
          name: 'line',
          type: 'line',
          showSymbol: false,
          data: data
        }]
      });
    }
  }
}
</script>

<style scoped>
#myECharts {
  width: 900px;
  height: 600px;
}
</style>
