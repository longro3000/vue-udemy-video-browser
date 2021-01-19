<template>
    <ul>
        <VideoListItem 
            v-for="video in videos"
            :video="video" 
            :key="video.etag"
            @videoSelect='onVideoSelect'
        >
        </VideoListItem>
    </ul>
</template>

<script>
import { defineComponent } from 'vue';
import VideoListItem from './VideoListItem.ts.vue'

export default defineComponent({
    name: 'VideoList',
    components: {
        VideoListItem
    },
    props: {
        videos: Array
    },
    methods: {
        onVideoSelect(video) {
            this.$emit('videoSelect', video);
        }
    }
});
</script>