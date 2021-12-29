<template>
  <div class="container" id="app">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoDetail :video="selectedVideo"/>
    <VideoList :videos="videos"  @videoSelect="onVideoSelect"></VideoList>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './components/SearchBar.vue'
import VideoList from './components/VideoList.vue'
import VideoDetail from './components/VideoDetail.vue'

const API_KEY = "AIzaSyD9dEYoMebTB3kPXqwi1nUXFfmERs3_GwY";
export default {
  name: 'App',
  components: {
    SearchBar,
    VideoList,
    VideoDetail
  },
  data() {
    return {
      videos:[],
      selectedVideo: null,
    }
  },
  methods: {
    onTermChange(searchTerm) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      })
      .then(response => {
      console.log(response.data.items);
        this.videos = response.data.items;
      });
      
    },
    onVideoSelect (video) {
        this.selectedVideo = video
        console.log(video);
    }
  }
}
</script>

<style>

</style>
