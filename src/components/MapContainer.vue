<template>
  <div id="container"></div>
</template>
<script>
import AMapLoader from "@amap/amap-jsapi-loader";

export default {
  name: "map-view",
	props: {
		center: {
			type: Array,
			default : function(){
				return [102.833669, 24.88149]
			},
			require: false
		},
		zoom: {
			type: Number,
      default: 11,
      required: false
		}
	},
  mounted() {
    this.initAMap();
  },
  unmounted() {
    this.map?.destroy();
  },
  methods: {
    initAMap() {
      AMapLoader.load({
        key: "22e55df1a13ebe37dd2458fb68471a67", // 申请好的Web端开发者Key，首次调用 load 时必填
        version: "2.0", // 指定要加载的 JSAPI 的版本，缺省时默认为 1.4.15
        plugins: [  
					"AMap.Scale",
					"AMap.HawkEye",
					"AMap.ToolBar",
					"AMap.AutoComplete",
					"AMap.PlaceSearch",
					"AMap.ControlBar",
					"AMap.MouseTool",
					"AMap.DragRoute",
					"AMap.MoveAnimation"
					], // 需要使用的的插件列表，如比例尺'AMap.Scale'等
      })
        .then((AMap) => {
          this.map = new AMap.Map("container", {
            // 设置地图容器id
            viewMode: "3D", // 是否为3D地图模式
            zoom: this.zoom, // 初始化地图级别
            center: this.center, // 初始化地图中心点位置
          });
					this.marker = new AMap.Marker({
						map: this.map,
						position: this.center,
						icon: "https://a.amap.com/jsapi_demos/static/demo-center-v2/car.png",
						// offset: new AMap.Pixel(-10, -2),
					})
        })
        .catch((e) => {
          console.log(e);
        });
    },
  },
};
</script>
<style scoped>
#container {
  width: 100%;
  height: 800px;
}
</style>
