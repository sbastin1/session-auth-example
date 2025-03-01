<template>
  <div class="container">
    <OrgNavbar />
    <slot />
  </div>
</template>

<script setup lang="ts">
import OrgNavbar from "~/components/organisms/OrgNavbar.vue";
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
}

:root {
  background-color: $background;
  font-family: Roboto, serif;
  color: white;
}

.container {
  margin: auto;
  max-width: 1280px;
}
</style>
