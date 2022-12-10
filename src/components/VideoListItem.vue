<template>
  <li class="list-group-item">
    <img :src="thumbnailsUrl" alt="images">
    {{video.snippet.title}}
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props:{
    video:{
      type:Object,
      required:true
    }
  },
  computed:{
    thumbnailsUrl (){
      return this.video.snippet.thumbnails.default.url
    }
  }
}
</script>

<style scoped>

</style>