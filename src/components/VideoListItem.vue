<template>
  <li class="list-group-item" @click="onVideoSelect()">
    <div class="d-flex">
      <div class="flex-shrink-0">
        <img :src="thumbnailsUrl" alt="images">
      </div>
      <div class="flex-grow-1 ms-3">
        {{ video.snippet.title }}
      </div>
    </div>
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: {
    video: {
      type: Object,
      required: true
    }
  },
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url
    }
  },
  methods:{
    onVideoSelect(){
      this.$emit('onVideoSelect' , this.video)
    }
  }
}
</script>

<style scoped>
li{
  cursor: pointer;
}
li:hover{
  background-color: #eee;
}
</style>