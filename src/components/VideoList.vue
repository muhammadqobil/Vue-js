<template>
  <div>
    <ul class="list-group col-sm-12 col-xs-12 col-md-12 col-lg-4 fle">
      <video-list-item v-for="video in videos" @onVideoSelect="videoSelect($event)" :video="video" :key="video.etag" />
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
  },
  methods:{
    videoSelect(video){
      this.$emit('onVideoSelect' , video)
    }
  }
}
</script>

<style scoped>

</style>