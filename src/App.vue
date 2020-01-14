<template>
  <app-layout>
    <div slot="controls">
      <div>/|CONTROLS GONNA WRAP|\</div>
      <button @click="updateCount(-1)">-</button>
      {{ count }}
      <button @click="updateCount(1)">+</button>
    </div>
    <div slot="reels" class="d-flex flex-row flex-nowrap">
      <div v-for="i in count" :key="i">
        <reel></reel>
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
import TextGen from "./components/TextGen";

export default {
  data() {
    return {
      count: 3
    };
  },
  methods: {
    updateCount(change) {
      this.count += change;
    }
  },
  components: {
    AppLayout: Layout,
    TextGen: TextGen,
    Reel: Reel
  }
};
</script>
<style scoped></style>
