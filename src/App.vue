<template>
    <div>
        <SearchBar @termChange="onTermChange"></SearchBar>
        <VideoList :videos="videos"></VideoList>

    </div>
</template>

<script>

import SearchBar from './components/SearchBar';
import VideoList from './components/VideoList';
import axios from 'axios';
const API_KEY = 'AIzaSyCbAjH1ngmMVWBZz2j8YFfszw5T9t_q8rQ';


export default {
  name: 'App',
  components: {
      SearchBar,
      VideoList
 
  },

  data(){
      return{
          videos: [],

      }
  },

  methods:{
      onTermChange: function(searchTerm){
          console.log(searchTerm);
          axios.get('https://www.googleapis.com/youtube/v3/search', {
              params: {
                  key: API_KEY,
                  type: 'video',
                  part: 'snippet',
                  q: searchTerm
              }
          }).then(response => {
              this.videos = response.data.items;
          });
      }
  }
  
};
</script>