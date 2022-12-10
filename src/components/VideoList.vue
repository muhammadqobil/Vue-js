<template>
  <div>
    <ul class="list-group">
      <video-list-item v-for="video in videos" :video="video" :key="video.etag" />
    </ul>
  </div>
</template>

<script>
import VideoListItem from "@/components/VideoListItem";
export default {
  name: "VideoList",
  components: {VideoListItem},
  props:{
    videos:{
      type:Array,
      required:true
    }
  }
}
</script>

<style scoped>

</style>