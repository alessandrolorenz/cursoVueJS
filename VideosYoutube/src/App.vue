<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <div class="row">
    <VideoDetail v-bind:video="selectedVideo"/>
    <VideoList @videoSelectParent="videoSelect" :videosArr="videos"></VideoList>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar"
import VideoList from "./components/VideoList"
import VideoDetail from "./components/VideoDetail"

const API_KEY = "AIzaSyCTfg4yfkpY-Lzs8nI_6Crmsbz5Gk-91Yw"

export default {
  nane: "App",
  components: {
    // SearchBar: SearchBar
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return { videos: [], selectedVideo: null }
  },
  methods: {
    onTermChange(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(resp => {
          // console.log(resp.data.items);
          this.videos = resp.data.items
        }).catch(err => console.log(err))
    },
    videoSelect(video) {
      // console.log(video)
      this.selectedVideo = video
    }
  }
};
</script>

<style>
</style>

