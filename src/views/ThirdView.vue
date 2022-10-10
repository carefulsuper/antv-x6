<template>
  <div class="third">
    <h1>you are my hero</h1>
    <div>
      <div class="myView" id="container"></div>
    </div>
  </div>
</template>
  
<script setup>
import { Graph, Shape } from '@antv/x6'
import { onMounted } from 'vue';
const rect = new Shape.Rect({
  id: 'node1',
  x: 40,
  y: 40,
  width: 100,
  height: 40,
  label: 'rect',
  zIndex: 2,
})
const circle = new Shape.Circle({
  id: 'node2',
  x: 280,
  y: 200,
  width: 60,
  height: 60,
  label: 'circle',
  zIndex: 2,
})

const edge = new Shape.Edge({
  id: 'edge1',
  source: rect,
  target: circle,
  zIndex: 1,
})


const init = () => {
  const graph = new Graph({
    panning: true,
    grid: {
      size: 20,
      visible: true,
      type: 'mesh', // 'dot' | 'fixedDot' | 'mesh'
      args: {
        color: '#000', // 网格线/点颜色
        thickness: 1,     // 网格线宽度/网格点大小
      },
    },
    container: document.getElementById('container'),
    width: 800,
    height: 600
  })
  graph.addNode(rect)
  graph.addNode(circle)
  graph.addEdge(edge)
  graph.addNode({
    x: 60,
    y: 60,
    width: 160,
    height: 80,
    label: 'Rect With Ports',
    ports: {
      groups: {
        group1: {
          attrs: {
            circle: {
              r: 6,
              magnet: true,
              stroke: '#31d0c6',
              strokeWidth: 2,
              fill: '#fff',
            },
          },
        },
      },
      items: [
        {
          id: 'port1',
          group: 'group1',
          attrs: {
            text: {          // 标签选择器
              text: 'port1', // 标签文本
            },
          },
        },
        {
          id: 'port2',
          group: 'group1',
          attrs: {
            text: {          // 标签选择器
              text: 'port2', // 标签文本
            },
          },
        },
        {
          id: 'port3',
          group: 'group1',
          attrs: {
            text: {          // 标签选择器
              text: 'port2', // 标签文本
            },
          },
        },
      ],
    },
  })
  graph.addNode({
    x: 60,
    y: 60,
    width: 160,
    height: 80,
    label: 'Rect With Ports',
    ports: [
      {
        id: 'port1',
        attrs: {
          circle: {
            r: 6,
            magnet: true,
            stroke: '#31d0c6',
            strokeWidth: 2,
            fill: '#fff',
          },
        },
      },
      {
        id: 'port2',
        attrs: {
          circle: {
            r: 6,
            magnet: true,
            stroke: '#31d0c6',
            strokeWidth: 2,
            fill: '#fff',
          },
        },
      },
      {
        id: 'port3',
        attrs: {
          circle: {
            r: 6,
            magnet: true,
            stroke: '#31d0c6',
            strokeWidth: 2,
            fill: '#fff',
          },
        },
      },
    ],
  })
}
console.log(typeof (rect))
onMounted(() => {
  init()
})
</script>