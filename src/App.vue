<template>
  <app-layout>
    <div slot="controls">
      <!--<div>/|CONTROLS ARE GONNA WRAP|\</div>
      <button @click="updateCount(-1)">-</button>
      {{ reel_count }}
      <button @click="updateCount(1)">+</button>
      <label>
        <input type="checkbox" id="xray" @click="goPerspective"/>
        Вид сбоку
      </label>-->
      <advanced-controls></advanced-controls>
    </div>
    <div slot="reels" class="d-flex flex-row flex-nowrap">
      <div v-for="i in reel_count" :key="i">
        <reel :reel-id="reel_count - 1" :slots-per-reel="8"></reel>
      </div>
    </div>
    <div slot="text-gen">
      <text-gen></text-gen>
    </div>
  </app-layout>
</template>
<script>
import Layout from "./components/Layout";
import Reel from "./components/Reel";
import AdvancedControls from "./components/controls/AdvancedControls";
import TextGen from "./components/TextGen";

export default {
  data() {
    return {
      // eslint-disable-next-line
      reel_count: 0,
      slots_per_reel: 8
    };
  },
  methods: {
    updateCount(change) {
      this.reel_count += change;
    },
    goPerspective() {
      let toggle = document.getElementById('xray');
      let myrings = document.querySelectorAll('ring');
      toggle.addEventListener("click", function(event) {
        event.preventDefault();
        for(let i = 0; i < this.reel_count; i++ ) {
          myrings[i].classList.toggle('perspective');
        }
      });
      /*
      document.querySelectorAll('ring').forEach((el) => {
        el.classList.toggle('perspective');
      });*/
    }
  },
  components: {
    AppLayout: Layout,
    TextGen: TextGen,
    Reel: Reel,
    AdvancedControls: AdvancedControls
  }
};
</script>
<style scoped></style>
