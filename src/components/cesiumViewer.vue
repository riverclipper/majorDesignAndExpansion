<template>
    <div id="cesiumContainer"></div>
</template>

<script>
//导入Cesium源码中的Viewer组件，注意这里是用的Viewer组件的方式加载，而不是加载整个Cesium
import Viewer from "cesium/Source/Widgets/Viewer/Viewer";
//我们刚才所说的如何让Cesium知道静态资源在哪里的API
import buildModuleUrl from "cesium/Source/Core/buildModuleUrl"
//导入必须的样式表
import "cesium/Source/Widgets/widgets.css";

export default{
    name:"cesiumContainer",
    mounted:function () {
        //设置静态资源目录
        buildModuleUrl.setBaseUrl('../../static/Cesium/')
        //创建viewer实例
       this.viewer = new Viewer('cesiumContainer', {
		    animation: false, // 是否显示动画控件
		    shouldAnimate: false, //是否初始时刻运动
		    homeButton: false, // 是否显示Home按钮
		    fullscreenButton: false, // 是否显示全屏按钮
		    baseLayerPicker: false, // 是否显示图层选择控件 去掉自带的图层选择器
		    geocoder: false, // 是否显示地名查找控件,设置为true，则无法查询
		    timeline: false, // 是否显示时间线控件
		    sceneModePicker: true, // 是否显示投影方式控件 三维/二维
		    navigationHelpButton: false, // 是否显示帮助信息控件
		    infoBox: false, // 是否显示点击要素之后显示的信息 信息框小部件
		    requestRenderMode: false, // true启用请求渲染模式:更新实体需拖动地图 视图才更新[true 加载完entity后requestRender一下]
		    scene3DOnly: false, // 每个几何实例将只能以3D渲染以节省GPU内存 如果设置为true，则所有几何图形以3D模式绘制以节约GPU资源
		    sceneMode: 2, // 初始场景模式 1 2D模式 2 2D循环模式 3 3D模式  Cesium.SceneMode
		    fullscreenElement: document.body, // 全屏时渲染的HTML元素
		    selectionIndicator : false,//是否显示选取指示器组件
		    terrainProvider: Cesium.createWorldTerrain(),// 注释时相当于使用默认地形，解开注释相当于使用全球地形[世界地形数据]
		    baseLayerPicker:false,
		    //imageryProvider:new Cesium.UrlTemplateImageryProvider({
		    //    url:"satellite/tiles/{type}/z={z}&x={x}&y={y}",
		    //})
		})
    },
    data () {
        return {
            'viewer' : {}
        }
    }
}
</script>

<style scoped>

</style>
