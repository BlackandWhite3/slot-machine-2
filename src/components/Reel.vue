<template>
  <div id="reel" class="reelContainer" v-once>
    <b-button pill variant="secondary">Очистить барабан</b-button>
    <div :id="'ring' + reelId" class="ring"></div>
  </div>
</template>

<script>
export default {
  name: "Reel",
  props: {
    reelId: Number,
    slotsPerReel: Number
  },
  data() {
    return {

      slotAngle: 0,
      reelRadius: 0,
      panelHeight: 188
    };
  },
  methods: {
    getSlotAngle(slotsPerReel) {
      return 360 / slotsPerReel;
    },
    getReelRadius(panelHeight, slotsPerReel) {
      return Math.round(panelHeight / 2 / Math.tan(Math.PI / slotsPerReel));
    }
  },
  /*Старый способ, перенесённый из jQuery*/
  mounted() {
    this.slotAngle = this.getSlotAngle(this.slotsPerReel);
    this.reelRadius = this.getReelRadius(this.panelHeight, this.slotsPerReel);
    for (let i = 0; i < 8; i++) {
      console.log(this.reelId);
      let slot = document.createElement("div");
      slot.className = "slot";
      slot.id = this.reelId + "-" + i;
      document.getElementById("ring" + this.reelId).append(slot);
      document.getElementById(this.reelId + "-" + i).append("Test");
      let MyTransform = "rotateX(" + (this.slotAngle * (i + 1)) + "deg) translateZ(" + (this.reelRadius) + "px)";
      document.getElementById(this.reelId + "-" + i).style.transform = MyTransform;
    }
  }
  /*Загрузка данных из API в Computed()
  computed() {}*/
};
</script>

<style scoped></style>
