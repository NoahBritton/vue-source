<script setup>
import { ref, reactive } from "vue";
import { createClient } from "pexels";
import { watch, onMounted } from "vue";

const client = createClient("mnSzZj08w9jfjkNJZaiG1qxiRxNLDWoPh3zQjPosnSiY52hr5r3C4lj9");

const collection = reactive({
  media: {},
});
const photo = reactive({
  title: "",
  photographer: "",
  photographer_url: "",
  url: "",
});

const index = ref(0);

async function getCollection() {
  // get the meta-data for all collections
  let result = await client.collections.all({ per_page: 1 });

  // get the id of first collection
  const id = result.collections[0].id;

  // get media for the collection
  result = await client.collections.media({ id, type: "photos", per_page: 6 });

  // cache the media meta-data
  collection.media = result.media;
}

async function loadImage() {
  photo.title = collection.media[index.value].alt;
  photo.photographer = collection.media[index.value].photographer;
  photo.photographer_url = collection.media[index.value].photographer_url;
  photo.url = collection.media[index.value].src.tiny;
}

watch(collection, () => {
  console.log("collection changed");

  if (collection.media.length > 0) {
    loadImage();
  }
});

onMounted(() => {
  console.log("onmounted");
  loadImage();
});

function next() {
  console.log(collection.media.length);
  let n = document.getElementById("next");
  let b = document.getElementById("back");
  if (index.value + 1 == collection.media.length - 1) {
    n.setAttribute("disabled", "disabled");
    index.value++;
  } else {
    n.removeAttribute("disabled");
    b.removeAttribute("disabled");
    index.value++;
  }
  loadImage();
}
function back() {
  let n = document.getElementById("next");
  let b = document.getElementById("back");
  if (index.value - 1 == 0) {
    b.setAttribute("disabled", "disabled");
    index.value--;
  } else {
    b.removeAttribute("disabled");
    n.removeAttribute("disabled");
    index.value--;
  }
  loadImage();
}
</script>

<template>
  <div id="slideshow">
    <div id="arrows">
      <button id="back" type="button" @click="back()" disabled>&lt;</button>
      <div id="photo">
        <img :src="photo.url" />
      </div>
      <button id="next" type="button" @click="next()">></button>
    </div>
    <div id="photo-info">
      <span>{{ "image " + (index + 1) + ": " }}{{ photo.title }}</span
      ><br /><span
        >Photographer:
        <a :href="photo.photographer_url" target="_blank">
          {{ photo.photographer }}
        </a></span
      >
    </div>
    <div id="source">
      <a href="http://pexels.com"></a><span>Images provided by Pexels.com</span>
    </div>
  </div>
</template>

<style scoped>
#title {
  font-size: 2vh;
}
#subtitle {
  font-size: 1.2vh;
}
img {
  display: inline-block;
  width: 50%;
}
#slideshow {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px;
}
#arrows {
  display: flex;
  align-items: center;
}
button {
  margin: 20px;
  border: 0;
  background-color: rgb(55, 59, 65);
  border-radius: 10px;
}
*:disabled {
  color: rgba(0, 0, 0, 0);
  border: 0;
  background-color: #7a7a7a00;
}
#photo-info,
#photo img {
  width: 400px;
}
#photo-info {
  padding: 20px;
  text-align: center;
}
#photo-info span {
  display: inline-block;
  margin-top: 8px;
}
#source img {
  width: 30px;
  margin-right: 5px;
}
</style>
