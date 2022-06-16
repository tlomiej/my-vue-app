<template>
  <div class="component">
    PROJ4

    <vaadin-button @click="showCoords">Coords</vaadin-button>
  </div>
</template>

<script>
import "@vaadin/vaadin-button";
import Proj4 from "proj4";

export default {
  name: "ProjectElement",
  methods: {
    showCoords: () => {
      console.log("cords");

      Proj4.defs([
        [
          "EPSG:4326",
          "+title=WGS 84 (long/lat) +proj=longlat +ellps=WGS84 +datum=WGS84 +units=degrees",
        ],
        [
          "EPSG:4269",
          "+title=NAD83 (long/lat) +proj=longlat +a=6378137.0 +b=6356752.31414036 +ellps=GRS80 +datum=NAD83 +units=degrees",
        ],
      ]);

      //I'm not going to redefine those two in latter examples.
      const project = Proj4("EPSG:4326", "EPSG:4269", [2, 5]);
      console.log(project, "<---");
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
