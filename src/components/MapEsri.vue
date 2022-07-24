<template>
  <div id="viewDiv"></div>
</template>



<script>
import { loadModules } from "esri-loader";
export default {
  name: "MapEsri",
  mounted() {
    this.loadMap();
  },
  methods: {
    loadMap() {
      loadModules(["esri/config", "esri/Map", "esri/views/MapView"], {
        css: true,
      }).then(([esriConfig, ArcGISMap, MapView]) => {
        console.log(ArcGISMap, MapView);

        //TODO
        esriConfig.apiKey = "test";

        const map = new ArcGISMap({
          basemap: "topo-vector",
        });

        this.view = new MapView({
          container: this.$el,
          map: map,
          center: [-118, 34],
          zoom: 8,
        });
      });
    },
  },
};
</script>

<style>
/* esri styles */
@import url("https://js.arcgis.com/4.4/esri/themes/light/main.css");
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}
#nav a {
  font-weight: bold;
  color: #2c3e50;
}
#nav a.router-link-exact-active {
  color: #42b983;
}
#viewDiv {
  position: absolute;
  top: 3.5rem;
  bottom: 0;
  left: 0;
  right: 0;
}
</style>