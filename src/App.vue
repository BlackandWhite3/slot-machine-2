<template>
  <div class="body-h100">
    <component :is="current_header"></component>
    <main>
      <reels :reel-set="reel_set"></reels>
      <div class="d-flex flex-row main-container">
        <component :is="current_controls" class="w-25"></component>
        <div class="text-center text-gen w-75">
          <div>{{ reel_set.data.reels[0] }}</div>
          <text-gen></text-gen>
        </div>
      </div>
    </main>
  </div>
</template>
<script>
import AuthHeader from "./components/header/AuthHeader";
import Reels from "./components/Reels";
import AdvancedControls from "./components/controls/AdvancedControls";
import TextGen from "./components/TextGen";

const axios = require("axios");

export default {
  data() {
    return {
      // eslint-disable-next-line
      reel_set: {
        data: {
          reels: [
            {
              id: 1,
              nodes: [8]
            },
            {
              id: 2,
              nodes: [8]
            },
            {
              id: 3,
              nodes: [8]
            }
          ]
        }
      },
      current_header: "AuthHeader",
      current_controls: "AdvancedControls"
    };
  },
  mounted() {
    axios
      .get("http://pazhurdev.herokuapp.com/api/default_reel_sets/1/")
      .then(response => (this.reel_set = response));
  },
  methods: {
    updateCount(change) {
      this.reel_count += change;
    },
    switchHeader() {
      if (this.current_header === "AuthHeader") {
        this.current_header = "ProfileHeader";
      } else {
        this.current_header = "AuthHeader";
      }
    },
    switchControls() {
      if (this.current_controls === "BasicControls") {
        this.current_controls = "AdvancedControls";
      } else {
        this.current_controls = "BasicControls";
      }
    },
    goPerspective() {
      let toggle = document.getElementById("xray");
      let myrings = document.querySelectorAll("ring");
      toggle.addEventListener("click", function(event) {
        event.preventDefault();
        for (let i = 0; i < this.reel_count; i++) {
          myrings[i].classList.toggle("perspective");
        }
      });
      /*
      document.querySelectorAll('ring').forEach((el) => {
        el.classList.toggle('perspective');
      });*/
    }
  },
  components: {
    TextGen: TextGen,
    Reels: Reels,
    AdvancedControls: AdvancedControls,
    AuthHeader: AuthHeader
  }
};
</script>
<style scoped lang="scss">
main {
  background-color: cadetblue;
  height: 93%;
}
header {
  background-color: yellowgreen;
  height: 100%;
}
.body-h100 {
  height: inherit;
}
.main-container {
  height: 75%;
}
.text-gen {
  height: 25%;
}
</style>
