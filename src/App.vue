<script>
import axios from 'axios';
import {store} from './store';

import HeaderApp from './components/HeaderApp.vue';
import MainApp from './components/MainApp.vue';
import FooterApp from './components/FooterApp.vue';

export default {
  
  data() {
    return {
      store
    }
  },

  components:{
    HeaderApp,
    MainApp,
    FooterApp,
  },

  methods:{

  findElements(category){
    console.log('cerco il elemento', this.store.userSearch);

    axios
    .get('https://api.themoviedb.org/3/search/' + category, {
      params: {
        api_key: 'e99307154c6dfb0b4750f6603256716d',
        language: 'it-IT',
        query: this.store.userSearch,
        
      }
    })
    .then((response) => {

      //MOVIES
      if( category == 'movie'){
        console.log(response.data.results)
        this.store.movies = response.data.results
      }

      // SERIES
      else if(category == 'tv'){
        console.log(response.data.results)
        this.store.series = response.data.results
      }
      
    })

  }

},

}

</script>

<template>

  <HeaderApp @search="findElements('movie'), findElements('tv')" />

  <MainApp />

  <FooterApp />

</template>

<style lang="scss">
  @use "./styles/main.scss";
</style>
