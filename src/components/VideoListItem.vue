<template>
  <li class="list-group-item media" @click="selectVideo">
    <img class="mr-3" :src="videoImageUrl" :alt="videoItem.title" />
    <div class="media-body">
       {{ videoItem.title }}
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    videoItem() {
      return this.video.snippet;
    },
    videoImageUrl() {
      return this.video.snippet.thumbnails.default.url;
    },
  },
  methods: {
    selectVideo() {
      this.$emit("selectVideo", this.video);
    },
  },
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>
