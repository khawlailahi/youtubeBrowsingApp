<template>
    <ul class="list-group">
        <VideoListItem  v-for="video in videos"
        :video="video"
        :key="video.id.videoId"
        @videoSelect="onVideoSelect"
        >
        </VideoListItem>

    </ul>
</template>
<script>
import VideoListItem from './VideoListItem';

export default {
    name: 'VideoLsit',
    components: {
        VideoListItem,
    },
    props: {
        videos: Array,
    },
    methods: {
        onVideoSelect (video) {
            this.$emit('videoSelect', video);
        }
    },
}
</script>
<style>

</style>