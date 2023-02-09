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
  methods:{},

}
</script>

<template>

    <main>
        
        <div v-for="movie in store.movies">

            <h2>
                {{ movie.title }}
            </h2>

            <h4>
                {{ movie.original_title }}
            </h4>

            <span>
                {{ movie.original_language }}
            </span>

            <span>
                {{ movie.vote_average }}
            </span>

        </div>
        
    </main>
 
</template>

<style lang="scss" scoped>

</style>
