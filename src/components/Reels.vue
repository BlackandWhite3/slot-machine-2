<template>
  <div id="reelsContainer" class="w-75">
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
          :style="[{ transform: 'rotateX(' + rotateAngle[reel - 1][slot - 1] + 'deg)' + ' translateZ(' + reelRadius + 'px)' }, { 'z-index': reelsCount - reel}]"
        > <!--slotAngle * slot-->
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
      currentSlots: [],
      rotateAngle: [ //Попробуй перенести в created, сделать динамическое формирование. В любом случае так оставлять не вариант.
              [0,0,0,0,0,0,0,0],
              [0,0,0,0,0,0,0,0],
              [0,0,0,0,0,0,0,0],
              [0,0,0,0,0,0,0,0],
              [0,0,0,0,0,0,0,0],
              [0,0,0,0,0,0,0,0],
              [0,0,0,0,0,0,0,0],
              [0,0,0,0,0,0,0,0]
      ]
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
    },
    reelSpin() {
      for (let i = 1; i <= this.reelsCount; i++) {
        console.log("123");
      }
    },
    setRotateAngle() {

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
    reelRadius() {
      return Math.round(
        this.panelHeight / 2 / Math.tan(Math.PI / this.slotsPerReel)
      );
    },
  },
  created() {
    for (let i = 0; i < this.reelsCount; i++) {
      for (let j = 1; j <= this.slotsPerReel; j++) {
        this.rotateAngle[i][j - 1] = this.slotAngle * j;
      }
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

<style scoped>
button,
p {
  margin: 5px 10px;
}
</style>
