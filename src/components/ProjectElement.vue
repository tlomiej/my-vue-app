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
        item-value-path="code"
        :items="projections"
        required
        @change="inEpsg = $event.target.selectedItem"
      ></vaadin-combo-box>
      <vaadin-combo-box
        placeholder="Select out EPSG"
        label="Out epsg"
        item-label-path="name"
        item-value-path="code"
        :items="projections"
        required
        @change="outEpsg = $event.target.selectedItem"
      ></vaadin-combo-box>
    </vaadin-form-layout>

    <br />

    <vaadin-button
      @click="
        () => {
          this.outGeometry = showCoords(
            this.inEpsg,
            this.outEpsg,
            this.inGeometry
          );
        }
      "
      >Calculate</vaadin-button
    >
  </div>
</template>

<script>
import "@vaadin/vaadin-button";
import "@vaadin/vaadin-text-field/vaadin-text-area";
import "@vaadin/form-layout";
import "@vaadin/combo-box";

import Proj4 from "proj4";
import { projections } from "./projections";

export default {
  data() {
    return {
      projections,
      inGeometry: "[2, 5]",
      outGeometry: "",
      inEpsg: "",
      outEpsg: "",
    };
  },
  name: "ProjectElement",
  methods: {
    showCoords: (inEpsg, outEpsg, inGeometry) => {
      console.log("cords", inEpsg);

      Proj4.defs([
        [inEpsg.code, inEpsg.proj],
        [outEpsg.code, outEpsg.proj],
      ]);

      return Proj4(inEpsg.code, outEpsg.code, JSON.parse(inGeometry));
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
