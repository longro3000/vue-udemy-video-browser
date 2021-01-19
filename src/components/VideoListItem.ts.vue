<template>
    <li @click="onVideoSelect">
        <img :src="thumbnailUrl"/>
        {{ video.snippet.title }}
    </li>
</template>
<script lang='ts'>
import { defineComponent } from 'vue';

export default defineComponent({
    name: 'VideoListItem',
    props: {
        video: Object
    },
    computed: {
        thumbnailUrl(): string {
            return this.video!.snippet.thumbnails.default.url;
        }
    },
    methods: {
        onVideoSelect() {
            this.$emit('videoSelect', this.video)
        }
    }
})
</script>