<template>
  <div>
    <e-charts :options="polar">this is a echart</e-charts>
  </div>
</template>

<script>
import ECharts from 'vue-echarts'
import 'echarts/lib/chart/line'
import 'echarts/lib/component/polar'

export default {
  name: 'EchartsDemo',
  components: { ECharts },
  data () {
    let lineData = []
    for (let i = 0; i <= 360; i++) {
      let t = i / 180 * Math.PI
      let r = Math.sin(2 * t) * Math.cos(2 * t)
      lineData.push([r, i])
    }
    // console.log(lineData)
    return {
      polar: {
        title: {
          text: '极坐标双数值轴'
        },
        legend: {
          data: ['line']
        },
        polar: {
          center: ['50%', '54%']
        },
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
          min: 0
        },
        series: [
          {
            coordinateSystem: 'polar',
            name: 'line',
            type: 'line',
            showSymbol: false,
            data: lineData
          }
        ],
        animationDuration: 2000
      }
    }
  }
}
</script>

<style scoped>
  .echarts {
    width: 600px;
    height: 400px;
  }
</style>
