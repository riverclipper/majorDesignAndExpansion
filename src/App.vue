<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import cesiumViewer from "./components/cesiumViewer.vue"
export default {
  name: 'App',
  components : {
    'cesiumViewer' : cesiumViewer
  }
}
</script>

<style>
/* 保证浏览器全屏幕显示，没有多余的白边 */
html, body, #cesiumContainer {
 width: 1000px; 
 height: 700px; 
 margin: 0; 
 padding: 0; 
 overflow: hidden;
}
</style>
