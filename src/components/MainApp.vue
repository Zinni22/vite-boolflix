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

    <main class="p-5">

        <div class="container">
            
            <span>FILM</span>

            <div class="film-container">

                <!-- FILM -->
                <div v-for="movie in store.movies" class="single-card">
                    
                    <img :src="generatePoster(movie.poster_path)" :alt="movie.title">

                    <div class="description-texts">

                        <p>
                            <strong>Title: </strong>
                            {{ movie.title }}
                        </p>

                        <p>
                            <strong>Original Title: </strong>
                            {{ movie.original_title }}
                        </p>

                        <p>
                            <strong>Language: </strong>
                            <img :src="generateFlag(movie.original_language)" :alt="original_language">
                        </p>

                        <div class="stars">
                            <strong>Vote: </strong>
                            <span v-for="n in generateVote(movie.vote_average)">
                                ★ 
                            </span>

                            <span v-for="n in (5 - generateVote(movie.vote_average))">
                                ☆ 
                            </span>
                        </div>

                        <p>
                            <strong>Overview: </strong>
                            {{ movie.overview }}
                        </p>

                    </div>

                </div>

            </div>


            <span>SERIE TV</span>

            <div class="film-container" >
                <!-- SERIE TV -->
            
                <div v-for="serie in store.series" class="single-card">
                    
                    <img :src="generatePoster(serie.poster_path)" :alt="serie.name">

                    <div class="description-texts">

                        <p>
                            <strong>Title: </strong>
                            {{ serie.name }}
                        </p>

                        <p>
                            <strong>Original Title: </strong>
                            {{ serie.original_name }}
                        </p>

                        <p>
                            <strong>Language: </strong>
                            <img :src="generateFlag(serie.original_language)" :alt="original_language">
                        </p>

                        <div class="stars">
                            <strong>Vote: </strong>
                            <span v-for="n in generateVote(serie.vote_average)">
                                ★ 
                            </span>

                            <span v-for="n in (5 - generateVote(serie.vote_average))">
                                ☆ 
                            </span>
                        </div>

                        <p>
                            <strong>Overview: </strong>
                            {{ movie.overview }}
                        </p>
                    </div>

                </div>

            </div>
        </div>
        
    </main>
 
</template>

<style lang="scss" scoped>

main{
    background-color: rgb(62, 62, 62);
    color: white;

    span{
        font-weight: bold;
    }

    .film-container{

        margin-top: 30px;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
        .single-card{
            width: calc(100% / 4 - 20px);
            position: relative;
            cursor: pointer;
            margin-bottom: 30px;

            img{
                width: 100%;
            }

            .description-texts{
                position: absolute;
                top: 0px;
                left: 0px;
                width: 100%;
                height: 100%;
                padding: 20px;
                font-size: 0.8rem;
                background-color: rgba(0, 0, 0, 0.8);
                border: 1px solid white;
                display: none;
                overflow: auto;
                img{
                    width: 40px;
                }

                .stars span{
                    color: yellow;
                }
            }

        }
        .single-card:hover{
            .description-texts{
                display: block;
            }

        }
    }

}

</style>
