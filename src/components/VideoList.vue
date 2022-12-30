<template>
<ul class="list-group col-md-4">
  <video-list-item
      v-for="video in videos"
      :key="video.etag"
      :video="video"
      @videoSelect="onVideoSelect"
  >
  </video-list-item>
</ul>
</template>

<script>
import VideoListItem from "@/components/VideoListItem.vue";

export default {
  name: "VideoList",
  components: {VideoListItem},
  props: ['videos'],
  methods: {
    onVideoSelect(video) {
      this.$emit('videoSelect', video);
    }
  }
}
</script>

<style scoped>

</style>
