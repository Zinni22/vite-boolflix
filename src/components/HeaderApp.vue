<script>
import {store} from '../store';

export default {
name: 'HeaderApp',

  data () {
      return{
        store,
      }
  },

  components:{},
  methods:{},

}
</script>

<template>

    <header>
        
        <input type="text" placeholder="Film o serie tv"
        v-model="store.userSearch"
        >

        <button @click="$emit('search')">
            Search
        </button>
        
    </header>
 
</template>

<style lang="scss" scoped>

</style>
