<template>
  <ul>
     <li v-for="video in videos" :key="video.id">
         {{video.title}}
         {{video.id}}
         {{video.view}}
     </li>
  </ul>
</template>

<script>

import VideoService from "../services/VideoService"

export default {
   name : "video-list",

   data(){
   return {
            videos: [],
          }
   },
   methods : {

      listVideos() { 
         VideoService.getAll().then(res => {
            this.videos = res.data;
            console.log(res.data);
         })
         .catch(e => {
            console.log(e);
         });

      }
  
  
  },

  mounted(){
     this.listVideos();
  }
}
</script> 

<style>

</style>