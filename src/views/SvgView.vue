<template>
    <div class="svg">
        <div >
        <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
            <circle cx="100" cy="50" r="40" stroke="green" stroke-width="2" fill="yellow" />
        </svg>
        <svg xmlns="http://www.w3.org/2000/svg" version="1.1">
            <polyline points="0,40 40,40 40,80 80,80 80,120 120,120 120,160"
                style="fill:white;stroke:red;stroke-width:4" />
        </svg>
        <svg height="210" width="500">
            <polygon points="200,10 250,190 160,210" style="fill:lime;stroke:purple;stroke-width:1" />
        </svg> 
    </div>
       <!-- <object data="test01.svg" type="image/svg+xml"></object> -->
       <iframe src="../components/Image/test01.svg"></iframe>
    </div>
</template>
<script setup>
</script>