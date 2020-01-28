<template>
  <div id="reelsContainer" class="w-75">
    <div :id="'myreel' + reel" class="reelContainer" v-for="reel in reelsCount" :key="reel">
      <b-button pill variant="secondary" class="w-90 align-self-center">Очистить</b-button>
      <div :id="'ring' + reel" class="ring">
        <div
          :id="reel + '-' + slot"
          class="slot"
          v-for="slot in slotsPerReel"
          :key="slot"
          :style="{transform: 'rotateX(' + (slotAngle * slot) + 'deg)' + ' translateZ(' + reelRadius + 'px)'}"
        >
          Test
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Reels",
  props: {
    reelSet: Object
  },
  data() {
    return {
      panelHeight: 188,
    };
  },
  methods: {},
  computed: {
    reelsCount() {
      return this.reelSet.data.reels.length;
    },
    slotsPerReel() {
      return this.reelSet.data.reels[0].nodes.length;
    },
    slotAngle() {
      return 360 / this.slotsPerReel;
    },
    reelRadius() {
      return Math.round(this.panelHeight / 2 / Math.tan(Math.PI / this.slotsPerReel));
    },
  },
  // mounted() {
  //   for (let i = 1; i <= this.reelsCount; i++) {
  //     for (let j = 1; j <= this.slotsPerReel; j++) {
  //       document.getElementById(i + '-' + j).append("Test");
  //       document.getElementById(i + '-' + j).style.transform = "rotateX(" + (this.slotAngle * j) + "deg) translateZ(" + this.reelRadius + "px)";
  //     }
  //   }
  // }
  /*Старый способ, перенесённый из jQuery*/
  // mounted() {
  //   for (let i = 0; i < 8; i++) {
  //     console.log(this.reelId);
  //     let slot = document.createElement("div");
  //     slot.className = "slot";
  //     slot.id = this.reelId + "-" + i;
  //     document.getElementById("ring" + this.reelId).append(slot);
  //     document.getElementById(this.reelId + "-" + i).append("Test");
  //     document.getElementById(this.reelId + "-" + i).style.transform = "rotateX(" + (this.slotAngle * (i + 1)) + "deg) translateZ(" + (this.reelRadius) + "px)";
  //   }
  // }
  /*Загрузка данных из API в Computed()
  computed() {}*/
};
</script>

<style scoped>
button,
p {
  margin: 5px 10px;
}
</style>
