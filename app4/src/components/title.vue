<script setup>
import { reactive } from "vue";
const header = reactive({
  title: "The Title",
  image: "src/assets/image.jpg",
});
const size = reactive({
  w: 200,
  h: 200,
});
</script>

<template>
  {{ header.title }}
  <img :src="header.image" :width="size.w" :height="size.h" />
</template>

<style></style>
