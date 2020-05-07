<template>
  <ul class="list-group col-md-4">
    <VideoListItem
      v-for="item in videos"
      :key="item.etag"
      :video="item"
      @selectVideo="selectVideo"
    />
  </ul>
</template>

<script>
import VideoListItem from "./VideoListItem";

export default {
  name: "VideoList",
  props: ["videos"],
  components: {
    VideoListItem,
  },
  methods: {
    selectVideo(video) {
      this.$emit("selectVideo", video);
    },
  },
};
</script>

<style scoped></style>
