<template>
  <div id="app" class="container">
    <search-bar @termChange="OnTermChange"/>
    <video-list :videos="videos" />
  </div>
</template>

<script>
import VideoList from "@/components/VideoList";
const API_KEY="AIzaSyBpWgrrIRwJF21sE-VlwViSou3KBLQQ3E0";
import SearchBar from "@/components/SearchBar";
import axios from 'axios'
export default {
  name: "App",
  components: {VideoList, SearchBar},
  data(){
    return{
      videos:[]
    }
  },
  methods:{
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
}
  }
}
</script>

<style scoped>

</style>