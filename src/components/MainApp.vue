<script>
import {store} from '../store';

export default {
name: 'MainApp',

  data () {
      return{
        store
      }
  },

  components:{},
  methods:{

    generateFlag(language){

        switch (language){
            case 'en':
            language = 'uk';
                break;
            
            case 'pt':
            language = 'po';
                break;
            case 'es':
            language = 'sp'
                break;
        };

        let flag = `https://www.worldometers.info//img/flags/small/tn_${language}-flag.gif`;
        return flag;
    }
  },

}
</script>

<template>

    <main>
        
        <h2>Movie</h2>
        <div v-for="movie in store.movies">

            <h3>
                {{ movie.title }}
            </h3>

            <h4>
                {{ movie.original_title }}
            </h4>

            <img :src="generateFlag(movie.original_language)" alt="">

            <p>
                {{ movie.vote_average }}
            </p>

        </div>

        <h2>Series</h2>
        <div v-for="serie in store.series">

            <h3>
                {{ serie.name }}
            </h3>

            <h4>
                {{ serie.original_name }}
            </h4>

            <img :src="generateFlag(serie.original_language)" alt="">

            <p>
                {{ serie.vote_average }}
            </p>

        </div>
        
    </main>
 
</template>

<style lang="scss" scoped>

</style>
