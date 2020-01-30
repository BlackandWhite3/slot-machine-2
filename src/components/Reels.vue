<template>
  <div id="reelsContainer">
    <div
      :id="'myreel' + reel"
      class="reelContainer"
      v-for="reel in reelsCount"
      :key="reel"
    >
      <b-button pill variant="secondary" class="w-90 align-self-center">Очистить</b-button>
      <div :id="'ring' + reel" class="ring" :style="{ transform: 'rotateY(8deg)' }"> <!--'rotateX(' + rotateAngle[reel - 1] + 'deg)' + -->
        <div
          :id="reel + '-' + slot"
          class="slot"
          v-for="slot in slotsPerReel"
          :key="slot"
          :style="{ transform: 'rotateX(' + slotsAngles[slot - 1] + 'deg)' + ' translateZ(' + reelRadius + 'px)' }"
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
      panelHeight: 144,
      currentSlots: []
    };
  },
  methods: {
    setCurrentSlots(setSlots) {
      for (let i = 1; i <= this.reelsCount; i++) {
        this.currentSlots[i - 1] = setSlots[i - 1];
      }
    },
    getRandomInt(min, max) {
      //Максимум и минимум включены
      min = Math.ceil(min);
      max = Math.floor(max);
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }
  },
  computed: {
    reelsCount() {
      return this.reelSet.data.reels.length;
    },
    slotsPerReel() {
      //Также указывает на выпадающий по умолчанию слот.
      // 8 ячеек - значит при первоначальной отрисовке в 1-м барабане на пользователя будет смотреть слот с id = "1-8"
      return this.reelSet.data.reels[0].nodes.length;
    },
    slotAngle() {
      return 360 / this.slotsPerReel;
    },
    slotsAngles() {
      let slotsAngles = [];
      for (let i = 1; i <= this.reelsCount; i++) {
        slotsAngles[i - 1] = this.slotAngle * i;
      }
      return slotsAngles;
    },
    reelRadius() {
      return Math.round(
        this.panelHeight / 2 / Math.tan(Math.PI / this.slotsPerReel)
      );
    }
  },
  updated() {
    //ВЫНЕСТИ В МЕТОД ПРИ ЗАГРУЗКЕ НАБОРА ИЗ API
    for (let i = 1; i <= this.reelsCount; i++) {
      this.currentSlots[i - 1] = this.slotsPerReel;
    }
  }
};
</script>

<style scoped lang="scss">
  $ring-height: 144px;
button, p {
  margin: 5px 10px;
}
  button {
    margin-bottom: $ring-height;
  }
  #reelsContainer {
  display: flex;
  flex-direction: row-reverse;
  justify-content: center;
    min-height: $ring-height * 3.5;
}
  .reelContainer {
  display: flex;
  flex-direction: column;
  min-height: inherit;
}
  .ring {
  margin: 0 auto;
  width: 150px;
  min-height: $ring-height;
  float: left;
  -webkit-transform-style: preserve-3d;
          transform-style: preserve-3d;
  -webkit-transition: transform 2s ease-in-out;
          transition: transform 2s ease-in-out;
}
.slot {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  position: absolute;
  width: inherit; /*90*/
  min-height: inherit; /*80*/
  box-sizing: border-box;
  opacity: 0.9;
  color: rgba(0, 0, 0, 0.9);
  background: #fff;
  border: solid 1px #000;
  text-align: center;
}
.slot > p {
  max-width: inherit;
  margin: 0 auto;
}
</style>
