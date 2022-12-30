<template>
  <div class="container">
    <search-bar @termChange="onTermChange"></search-bar>
    <div class="row">
      <video-detail :video="selectedVideo"></video-detail>
      <video-list :videos="videos" @videoSelect="onVideoSelect"></video-list>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from "@/components/SearchBar.vue";
import VideoList from "@/components/VideoList.vue";
import VideoDetail from "@/components/VideoDetail.vue";
const API_KEY = 'AIzaSyBdHjiAMMEr7WRV0Sau8vNCX9GDocdTyCo'

export default {
  name: 'App',
  components: {VideoDetail, VideoList, SearchBar},
  data() {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onTermChange(searchTerm) {
      axios.get(`https://www.googleapis.com/youtube/v3/search`, {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => {
        this.videos = response.data.items
      })
    },
    onVideoSelect(video) {
      this.selectedVideo = video;
    }
  }
}
</script>

<style>

</style>
