<template>
  <div id="app" class="container">
    <search-bar @termChange="OnTermChange"/>
    <div class="row">
      <video-detail :video="selectVideo" />
      <video-list @onVideoSelect="videoSelect($event)" :videos="videos" />
    </div>
  </div>
</template>

<script>
const buttons = document.querySelectorAll('button')
// import VideoList from "@/components/VideoList";
import SearchBar from "@/components/SearchBar";
const API_KEY="AIzaSyBpWgrrIRwJF21sE-VlwViSou3KBLQQ3E0";
import axios from 'axios'
import VideoDetail from "@/components/VideoDetail";
import VideoList from "@/components/VideoList";
export default {
  name: "App",
  components: {VideoList, VideoDetail, SearchBar},
  data(){
    return{
      videos:[],
      selectVideo:null
    }
  },
  methods:{
    videoSelect(video){
      this.selectVideo = video
    },
    OnTermChange(searchTerm){
      axios.get('https://www.googleapis.com/youtube/v3/search',{
        params:{
          key:API_KEY,
          type:'video',
          part:'snippet',
          q:searchTerm
        }
      }).then(response=>{
        this.videos.splice(0,this.videos.length,...response.data.items)
      }).catch(error=>{
        console.log(error)
      })
    },
    addClass(){
      console.log(buttons)
      buttons.forEach(item=>{
        console.log(item)
      })
    }
  },
}
</script>

<style scoped>

</style>