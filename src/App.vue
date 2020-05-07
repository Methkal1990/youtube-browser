<template>
  <div>
    <h1>Video Browser</h1>
    <div class="container">
      <SearchBar @updateSearch="updateSearch" />

      <div class="row">
        <VideoDetails :selectedVideo="selectedVideo" />
        <VideosList :videos="videos" @selectVideo="selectVideo" />
      </div>
    </div>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
import VideosList from "./components/VideosList";
import VideoDetails from "./components/VideoDetails";

import axios from "axios";

// git this key from Google Developer Console
const API_KEY = "***************************";

export default {
  name: "App",
  data() {
    return {
      videos: [],
      selectedVideo: null,
    };
  },
  components: {
    SearchBar,
    VideosList,
    VideoDetails,
  },
  methods: {
    updateSearch(term) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: term,
          },
        })
        .then((response) => {
          this.videos = response.data.items;
        })
        .catch((error) => console.log(error));
    },
    selectVideo(video) {
      this.selectedVideo = video;
    },
  },
  created() {
    this.updateSearch("vue");
    console.log(this.videos)
  },
};
</script>

<style scoped>
h1 {
  text-align: center;
  margin-top: 2rem;
}
.container {
  padding: 1rem;
}
</style>
