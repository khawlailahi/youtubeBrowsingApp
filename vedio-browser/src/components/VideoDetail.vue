<template>
    <div v-if="video">
        {{ video.snippet.title}}
    </div>
</template>

<script>
export default {
    name: 'VideoDetail',
    props: {
        video: Object,
    }
}
</script>

<style>
</style>