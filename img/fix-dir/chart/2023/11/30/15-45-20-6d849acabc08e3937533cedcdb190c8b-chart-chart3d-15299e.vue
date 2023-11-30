<template>
  <div>
    <div id= 'echart3d' ref="chart" style="height: 400px" />
  </div>
</template>

<script>
import * as echarts from 'echarts'
import 'echarts-gl'
export default {
  mounted() {
    this.drawChart()
  },
  methods: {
    drawChart() {
      // document.getElementById('echart3d')
      const chart = echarts.init(document.getElementById('echart3d'))

      const data = [
        {
          'id': 0,
          'tag': 't_{0}',
          'endpoint': 'Endpoint 0',
          'color': '#2ecc71',
          'attributes': [
            18,
            11,
            5
          ]
        },
        {
          'id': 1,
          'tag': 't_{1}',
          'endpoint': 'Endpoint 0',
          'color': '#2ecc71',
          'attributes': [
            33,
            7,
            11
          ]
        },
        {
          'id': 4,
          'tag': 't_{4}',
          'endpoint': 'Endpoint 0',
          'color': '#2ecc71',
          'attributes': [
            9,
            12,
            3
          ]
        },
        {
          'id': 6,
          'tag': 't_{6}',
          'endpoint': 'Endpoint 2',
          'color': '#3498db',
          'attributes': [
            6,
            25,
            10
          ]
        },
        {
          'id': 7,
          'tag': 't_{7}',
          'endpoint': 'Endpoint 1',
          'color': '#1abc9c',
          'attributes': [
            31,
            8,
            6
          ]
        }]

      const seriesData = data.map((item) => ({
        name: item.endpoint,
        type: 'scatter3D',
        symbolSize: 10,
        // 控制点的透明度
        itemStyle: {
          opacity: 0.8
        },
        data: [[item.attributes[0], item.attributes[1], item.attributes[2]]]
      }))

      // 绘制3D散点图
      chart.setOption({
        // 图表标题
        legend: {
          data: data.map((item) => item.endpoint)
        },
        title: {
          text: 'ECharts 3D Scatter Plot Demo'
        },
        // 图表类型，3D散点图
        series: seriesData,
        // X轴的3D坐标系，相关设置
        xAxis3D: {
          type: 'value',
          name: '属性1',
          scale: true,
          inverse: false // 是否是反向坐标轴
        },
        // Y轴的3D坐标系，相关设置
        yAxis3D: {
          type: 'value',
          scale: true
        },
        // Z轴的3D坐标系，相关设置
        zAxis3D: {
          type: 'value',
          scale: true
        },
        // 旋转3D图表
        grid3D: {
          viewControl: {
            // 摄像机视角
            alpha: 45,
            beta: 30
          }
        }
      })
    }
  }
}
</script>

<style scoped>
</style>
