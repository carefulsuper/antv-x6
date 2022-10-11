<template>
    <div class="group">
        <h1>Group</h1>
        <div>
            <div id="container"></div>
        </div>
    </div>
</template>

<script setup>
import { Graph } from '@antv/x6'
import { onMounted } from 'vue';
const init = () => {
    const graph = new Graph({
        embedding: {
            enabled: true,
            findParent({ node }) {
                const bbox = node.getBBox()
                return this.getNodes().filter((node) => {
                    // 只有 data.parent 为 true 的节点才是父节点
                    const data = node.getData()
                    if (data && data.parent) {
                        const targetBBox = node.getBBox()
                        return bbox.isIntersectWithRect(targetBBox)
                    }
                    return false
                })
            },
  },
        
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

    const child1 = graph.addNode({
        x: 120,
        y: 80,
        width: 120,
        height: 60,
        zIndex: 10,
        label: 'Child\n(embedded)',
        attrs: {
            body: {
                fill: 'green',
            },
            label: {
                fill: '#fff',
            },
        },
    })
    const child2 = graph.addNode({
        x: 300,
        y: 200,
        width: 120,
        height: 60,
        zIndex: 10,
        label: 'Child\n(out)',
        attrs: {
            body: {
                fill: 'yellow',
            },
            label: {
                fill: '#fff',
            },
        },
    })


    const parent = graph.addNode({
        x: 80,
        y: 40,
        width: 320,
        height: 240,
        zIndex: 1,
        label: 'Parent\n(try to move me)',
        //设置之后进入它的子节点才会变
        data:{
            parent:true
        }
    })
    graph.addEdge({
        source: child2,
        target: child1,
        vertices: [
            { x: 100, y: 200 },
            { x: 300, y: 120 },
        ],
    })
    parent.addChild(child1)
    parent.addChild(child2)
}

onMounted(() => {
    init()
})
</script>