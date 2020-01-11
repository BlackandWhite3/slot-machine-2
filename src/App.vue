<template>
  <app-layout>
    <div slot="auth-panel">
      <app-auth></app-auth>
    </div>
    <div slot="controls">
      <div>/|CONTROLS GONNA WRAP|\</div>
    </div>
    <div slot="reels">
      <div>/|REELS WON'T WRAP|\</div>
    </div>
    <div slot="text-gen">
      <div>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed et justo a nisi rhoncus posuere. Curabitur ultricies pharetra erat, at rhoncus purus cursus feugiat. Aenean rutrum est quis pretium ultricies. Quisque bibendum non augue ut ornare. Curabitur a lacus id odio imperdiet dapibus vitae egestas felis. Donec malesuada sagittis mauris, ac auctor libero pretium id. Morbi urna lorem, volutpat ut convallis et, pellentesque at nunc. Nam lacinia turpis id ante vulputate dictum. Sed quis nulla posuere, feugiat mi faucibus, porta sapien. Integer sodales, purus eget imperdiet condimentum, lectus orci consequat sem, ut laoreet magna velit semper libero. Donec efficitur maximus nisl, a maximus quam porttitor ut. Nulla in diam rhoncus, pulvinar metus nec, sollicitudin nibh. Fusce at fringilla nibh, eget euismod nunc. Cras condimentum velit nec felis posuere, quis molestie orci suscipit.
      </div>
    </div>
  </app-layout>
</template>
<script>
import Layout from "./components/Layout";
import AuthPanel from "./components/AuthPanel";

export default {
  data() {
    return {
      reels: []
    };
  },
  components: {
    AppLayout: Layout,
    AppAuth: AuthPanel
  }
};
</script>
<style scoped></style>
