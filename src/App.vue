<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js + TypeScript App"/>
  <SearchBar @termChange="onTermChange"/>
  <video-detail :video='selectedVideo'/>
  <VideoList
    @videoSelect="onVideoSelect" 
    :videos="videos"
  />
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import axios from 'axios';

import HelloWorld from './components/HelloWorld.vue';
import SearchBar from './components/SearchBar.ts.vue';
import VideoList from './components/VideoList.ts.vue';
import VideoDetail from './components/VideoDetail.ts.vue';

const API_KEY = 'AIzaSyCz8itc0ujQKjk9AxYe0mEuKxnM46co6H4';

interface DataType {
  videos: any[],
  selectedVideo: any
}

export default defineComponent({
  name: 'App',
  components: {
    HelloWorld,
    SearchBar,
    VideoList,
    VideoDetail,
  },
  data(): DataType {
    return {
      videos: [],
      selectedVideo: null
    }
  },
  methods: {
    onTermChange(searchTerm: string) {
      axios.get('https://www.googleapis.com/youtube/v3/search', {
        params: {
          key: API_KEY,
          type: 'video',
          part: 'snippet',
          q: searchTerm
        }
      }).then(response => {this.videos = response.data.items});
    },
    onVideoSelect(video: any) {
      this.selectedVideo = video
    }
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
