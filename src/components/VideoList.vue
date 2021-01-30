<template>
    <ul>
        Video list here
        {{videos.length}}
    </ul>
</template>



<script>

import VideoListItem from './VideoListItem'

export default {
    name: 'VideoList',
    props: ['videos']
}
</script>

<style>

</style>