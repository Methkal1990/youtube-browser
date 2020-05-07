<template>
  <div class="col-md-8">
    <div v-if="selectedVideo" class="embed-responsive embed-responsive-16by9">
      <iframe
        class="embed-responsive-item"
        width="560"
        height="315"
        :src="videoUrl"
      ></iframe>
    </div>
    <div v-if="selectedVideo" class="details">
      <h4>{{ selectedVideo.snippet.title }}</h4>
      <p>{{ selectedVideo.snippet.description }}</p>
    </div>
    <div v-else class="embed-responsive embed-responsive-16by9">
      <iframe
        class="embed-responsive-item"
        width="560"
        height="315"
        src="https://www.youtube.com/embed/"
      ></iframe>
    </div>
  </div>
</template>

<script>
export default {
  name: "VideoDetails",
  props: ["selectedVideo"],
  computed: {
    videoUrl() {
      return `https://www.youtube.com/embed/${this.selectedVideo.id.videoId}`;
    },
  },
};
</script>

<style scoped>
.details {
  margin-top: 10px;
  padding: 10px;
  border: 1px solid #ddd;
  border-radius: 4px;
}
</style>
