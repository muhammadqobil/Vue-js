<template>
  <div v-if="video" class="col-sm-12 col-xs-12 col-md-8 col-lg-8">
    <div class="ratio ratio-16x9">
      <iframe :src="videoUrl" allowfullscreen />
    </div>
    <div class="detail">
      <h4>
        {{ video.snippet.title }}
      </h4>
      <p>{{video.snippet.description}}</p>
    </div>
  </div>
</template>

<script>

export default {
  name: "VideoDetail",
  props: {
    video: {
      type: Object,
      required: false
    }
  },
  computed:{
    videoUrl(){
      const videoId=this.video.id.videoId ;
      return 'https://www.youtube.com/embed/' + videoId
    }
  }
}
</script>

<style scoped>
.detail{
  margin-top: 10px;
  padding: 10px;
  border-radius: 4px;
  border: 1px solid #ddd;
}
</style>