<template>
  <div class="body-h100">
    <auth-header></auth-header>
    <main class="main">
      <div class="d-flex flex-row-reverse main-container">
        <slot name="reels"></slot>
        <slot name="controls"></slot>
      </div>
      <div class="text-center text-gen">
        <slot name="text-gen"></slot>
      </div>
    </main>
  </div>
</template>

<script>
import AuthHeader from "./header/AuthHeader";

export default {
  name: "Layout",
  data() {
    return {};
  },
  components: {
    AuthHeader: AuthHeader
  }
};
</script>

<style scoped lang="scss">
header {
  background-color: yellowgreen;
  height: 7%;
}
main {
  background-color: cadetblue;
  height: 93%;
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
