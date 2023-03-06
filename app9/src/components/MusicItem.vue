<script setup>
import { ref, onMounted } from "vue";

const audio = ref(null);
const props = defineProps(["song", "title"]);
const song = props.song;
const title = props.title;

function getAudioUrl() {
  return new URL(song, window.location.href);
}

onMounted(() => {
  audio.value.src = getAudioUrl();
});
</script>

<template>
  <h3>{{ title }}</h3>
  <audio ref="audio" controls></audio>
</template>

<style></style>
