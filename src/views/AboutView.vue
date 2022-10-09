<template>
  <div class="about" id="container">
  </div>
</template>
 
<script>
import { Graph } from '@antv/x6';
const data = {
  panning:true,
  // 节点
  nodes: [
    {
      id: 'node1', // String，可选，节点的唯一标识
      x: 40,       // Number，必选，节点位置的 x 值
      y: 40,       // Number，必选，节点位置的 y 值
      width: 80,   // Number，可选，节点大小的 width 值
      height: 40,  // Number，可选，节点大小的 height 值
      label: 'hello', // String，节点标签
    },
    {
      id: 'node2', // String，节点的唯一标识
      x: 160,      // Number，必选，节点位置的 x 值
      y: 180,      // Number，必选，节点位置的 y 值
      width: 80,   // Number，可选，节点大小的 width 值
      height: 40,  // Number，可选，节点大小的 height 值
      label: 'world', // String，节点标签
    },
    {
      id: 'node3', // String，可选，节点的唯一标识
      x: 80,       // Number，必选，节点位置的 x 值
      y: 80,       // Number，必选，节点位置的 y 值
      width: 80,   // Number，可选，节点大小的 width 值
      height: 40,  // Number，可选，节点大小的 height 值
      label: '猪猪侠', // String，节点标签
    },
  ],
  // 边
  edges: [
    {
      source: 'node1', // String，必须，起始节点 id
      target: 'node2', // String，必须，目标节点 id
      // eslint-disable-next-line no-dupe-keys
      target: 'node3', // String，必须，目标节点 id
    },
  ],
  container: document.getElementById('container'),
  width: 800,
  height: 600,
};
 
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "index",
  mounted () {
    this.init();
    // this.graph.zoom(0.2) // 获取缩放级别
    this.graph.drawBackground({color: 'yellow',})
  },
  methods: {
    init(){
      new Graph({
        //支持画布的平移拖拽
        panning: true,
        modifiers: 'shift',
        //看到画布
  //       scroller: {
  //   enabled: true,
  //   pannable: true,
  //   pageVisible: true,
  //   pageBreak: false,
  // },
  // mousewheel: {
  //   enabled: true,
  //   modifiers: ['ctrl', 'meta'],
  // },
        container: document.getElementById('container'),
        background: true,
        width: 800,
        height: 600,
      }).fromJSON(data)
    }
  }
}
 
</script>
 
<style scoped>
 
</style>