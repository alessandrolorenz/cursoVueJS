<template>
  <ul class="list-group col-md-4">
    <VideoListItem 
      v-for="singleVideo in videosArr" 
      :video="singleVideo"
      :key="singleVideo.etag"
      @videoSelect="videoSelectParent"
      >
      </VideoListItem>
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  components: {
    VideoListItem
  },
  props: {
    videosArr: Array
  },
  methods: {
    videoSelectParent(video) {
      this.$emit('videoSelectParent', video)
    }
  },
};
</script>

