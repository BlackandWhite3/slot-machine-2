<template>
  <div class="full-height">
    <header class="d-flex justify-content-end align-items-center">
      <slot name="auth-panel"></slot>
    </header>
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
export default {
  name: "Layout"
};
</script>

<style scoped>
header {
  background-color: yellowgreen;
  height: 7%;
}
main {
  background-color: cadetblue;
  height: 93%;
}
.full-height {
  height: inherit;
}
.main-container {
  height: 75%;
}
.text-gen {
  height: 25%;
}
</style>
