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

  findMovies(){
    console.log('cerco il film', this.store.userSearch);

    axios
    .get('https://api.themoviedb.org/3/search/movie', {
      params: {
        api_key: 'e99307154c6dfb0b4750f6603256716d',
        query: this.store.userSearch,
      }
    })
    .then((response) => {
      console.log(response.data.results)

      this.store.movies = response.data.results
    })
  }

},

}

</script>

<template>

  <HeaderApp @search="findMovies()" />

  <MainApp />

  <FooterApp />

</template>

<style lang="scss">
  @use "./styles/main.scss";
</style>
