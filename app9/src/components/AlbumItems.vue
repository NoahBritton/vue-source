<script setup>
import { onMounted } from "vue";
import MusicItem from "./MusicItem.vue";

const props = defineProps(["data"]);

function createURL(url) {
  return new URL(url, window.location.href);
}

function underScore(string) {
  return string.replace(/ /g, "_");
}
</script>

<template>
  <div v-for="item in props.data">
    <div class="card" style="width: 25rem">
      <div :id="`accordion${underScore(item.album.title)}`">
        <button
          class="btn btn-link"
          data-bs-toggle="collapse"
          :data-bs-target="`#collapse${underScore(item.album.title)}`"
          aria-expanded="false"
          :aria-controls="`collapse${underScore(item.album.title)}`"
          align-items-center
        >
          <img
            class="card-img-top"
            :src="createURL(item.album.art)"
            style="width: 350px; margin-left: 10px"
          />
        </button>
        <div class="card-body">
          <h5 class="card-title">
            {{ item.album.title }} -
            <span text-muted>{{ item.album.type }}</span>
          </h5>

          <p class="card-text">
            <a :href="item.album.link.spotify" class="card-link"
              ><i class="fa fa-spotify" style="font-size: 24px; color: #1db954"></i
            ></a>
            <a :href="item.album.link.appleMusic" class="card-link"
              ><i class="fa fa-apple" style="font-size: 24px; color: black"></i
            ></a>
            <a :href="item.album.link.youtube" class="card-link"
              ><i class="fa fa-youtube-play" style="font-size: 24px; color: red"></i
            ></a>
          </p>
        </div>
        <div
          :id="`collapse${underScore(item.album.title)}`"
          class="collapse"
          :aria-labelledby="`heading${underScore(item.album.title)}`"
          :data-bs-parent="`#accordion${underScore(item.album.title)}`"
        >
          <ul class="list-group list-group-flush" v-for="song in item.songList">
            <li class="list-group-item">
              <MusicItem :song="song.link" :title="song.title" />
            </li>
          </ul>
        </div>
      </div>
      <div :id="`accordion${underScore(item.album.title)}Links`">
        <div class="card">
          <div class="card-header" :id="`heading${underScore(item.album.title)}Links`">
            <h5 class="mb-0">
              <button
                class="btn btn-link"
                data-bs-toggle="collapse"
                :data-bs-target="`#collapse${underScore(item.album.title)}Links`"
                aria-expanded="false"
                :aria-controls="`collapse${underScore(item.album.title)}Links`"
              >
                Check out {{ item.artist.name }} through their official links
              </button>
            </h5>
          </div>

          <div
            :id="`collapse${underScore(item.album.title)}Links`"
            class="collapse"
            :aria-labelledby="`heading${underScore(item.album.title)}Links`"
            :data-bs-parent="`#accordion${underScore(item.album.title)}Links`"
          >
            <div class="card-body text-center">
              <a :href="item.artist.link.spotify" class="card-link"
                ><i class="fa fa-spotify" style="font-size: 24px; color: #1db954"></i
              ></a>
              <a :href="item.artist.link.appleMusic" class="card-link"
                ><i class="fa fa-apple" style="font-size: 24px; color: black"></i
              ></a>
              <a :href="item.artist.link.youtube" class="card-link"
                ><i class="fa fa-youtube-play" style="font-size: 24px; color: red"></i
              ></a>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style></style>
