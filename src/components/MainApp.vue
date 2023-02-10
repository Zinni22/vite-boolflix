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

    // FUNZIONE PER GENERARE LE BANDIERE
    generateFlag(language){

        //switch per trovare le bandiere corrette
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
    },

    //FUNZIONE PER GENRARE LE IMMAGINI
    generatePoster(image){

        let poster = `https://image.tmdb.org/t/p/w342${image}`;
        return poster;

    },

    //FUNZIONE PER TRASFORMARE DA 1 A 5
    generateVote(oldVote){

        console.log('voto di partenza', oldVote)

        let generatedVote = Math.ceil(oldVote / 2);
        console.log('voto di finale', generatedVote);

        return generatedVote;
        
    }
  },

}
</script>

<template>

    <main>

        <!-- FILM -->
        <h2>Movie</h2>
        <div v-for="movie in store.movies">

            <h3>
                {{ movie.title }}
            </h3>

            <img :src="generatePoster(movie.poster_path)" :alt="movie.title">

            <h4>
                {{ movie.original_title }}
            </h4>

            <img :src="generateFlag(movie.original_language)" :alt="original_language">

            <div>
                <span v-for="n in generateVote(movie.vote_average)">
                    ★ 
                </span>

                <span v-for="n in (5 - generateVote(movie.vote_average))">
                    ☆ 
                </span>
            </div>

        </div>

        <!-- SERIE TV -->
        <h2>Series</h2>
        <div v-for="serie in store.series">

            <h3>
                {{ serie.name }}
            </h3>

            <img :src="generatePoster(serie.poster_path)" :alt=" serie.name">

            <h4>
                {{ serie.original_name }}
            </h4>

            <img :src="generateFlag(serie.original_language)" :alt="original_language">

            <div>
                <span v-for="n in generateVote(serie.vote_average)">
                    ★ 
                </span>

                <span v-for="n in (5 - generateVote(serie.vote_average))">
                    ☆ 
                </span>
            </div>

        </div>
        
    </main>
 
</template>

<style lang="scss" scoped>

div{
    margin-bottom: 70px;
}

</style>
