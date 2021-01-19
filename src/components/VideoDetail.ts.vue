<template>
    <div v-if="video">
        <div>
            <iframe :src="videoUrl" />
        </div>
        {{ video.snippet.title }}
    </div>
</template>
<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'VideoDetail',
  props: {
      video: Object
  },
  computed: {
      videoUrl() {
          return `https://www.youtube.com/embed/${this.video.id.videoId}`;
      }
  }   
})
</script>