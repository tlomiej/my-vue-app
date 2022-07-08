<template>
  <div class="component">
    <vaadin-form-layout>
      <vaadin-text-area
        label="Geometry in"
        :value="inGeometry"
        @input="inGeometry = $event.target.value"
      ></vaadin-text-area>
      <vaadin-text-area
        label="Geometry out"
        :value="outGeometry"
        @input="outGeometry = $event.target.value"
      ></vaadin-text-area>

      <vaadin-combo-box
       placeholder="Select in EPSG"
        label="In epsg"
        item-label-path="name"
        item-value-path="id"
        :items="projections"
        @change="(e) => {
                        this.inEpsg = e.target.value;

                    }"
      ></vaadin-combo-box>
      <vaadin-combo-box
       placeholder="Select out EPSG"
        label="Out epsg"
        item-label-path="name"
        item-value-path="id"
        :items="projections"
      ></vaadin-combo-box>
    </vaadin-form-layout>

    <br />

    <vaadin-button @click="() => {
      this.outGeometry = showCoords(this.inEpsg, this.inGeometry)}">Coords</vaadin-button>
    {{ this.inGeometry }}
    {{ this.inEpsg }}
  </div>
</template>

<script>
import "@vaadin/vaadin-button";
import "@vaadin/vaadin-text-field/vaadin-text-area";
import "@vaadin/form-layout";
import "@vaadin/combo-box";

import Proj4 from "proj4";

export default {
  data() {
    return {
      projections: [
        { code: "EPSG: 4326", name: "EPSG: 4326" },
        { code: "EPSG: 2180", name: "EPSG: 2180" },
      ],
      inGeometry: "[2, 5]",
      outGeometry: "",
      inEpsg: '',
      outEpsg: '',
    };
  },
  name: "ProjectElement",
  methods: {
    showCoords: (inEpsg, inGeometry) => {
      console.log("cords", inEpsg);

      Proj4.defs([
        [
          "EPSG:4326",
          "+title=WGS 84 (long/lat) +proj=longlat +ellps=WGS84 +datum=WGS84 +units=degrees",
        ],
        [
          "EPSG:4269",
          "+title=NAD83 (long/lat) +proj=longlat +a=6378137.0 +b=6356752.31414036 +ellps=GRS80 +datum=NAD83 +units=degrees",
        ],
        [
          "EPSG:2180",
          "+proj=tmerc +lat_0=0 +lon_0=19 +k=0.9993 +x_0=500000 +y_0=-5300000 +ellps=GRS80 +towgs84=0,0,0,0,0,0,0 +units=m +no_defs",
        ],
      ]);

      //I'm not going to redefine those two in latter examples.
      return Proj4(inEpsg, "EPSG:2180", JSON.parse(inGeometry));


    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
vaadin-text-area {
  width: 100%;
  min-height: 200px;
  max-height: 550px;
}
</style>
