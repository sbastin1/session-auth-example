<template>
  <button>
    {{ text }}
  </button>
</template>

<script setup lang="ts">
defineProps({
  text: {
    type: String,
    default: "Button",
  },
});
</script>

<style scoped lang="scss">
button {
  background-color: $primary_accent;
  border: 0;
  padding: 15px;
  border-radius: 4px;
}
</style>
