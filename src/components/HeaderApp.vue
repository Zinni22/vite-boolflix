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

      <span><a href="#">
        BOOLFLIX
      </a></span>
        
        <form action="" @submit.prevent="$emit('search')">
          <input type="text" placeholder="Ricerca Film e Serie tv"
          v-model="store.userSearch"
          >

          <button>
              Cerca
          </button>
        </form>
        
    </header>
 
</template>

<style lang="scss" scoped>

header{
  background-color: black;
  height: 60px;
  padding: 0px 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;

  span a{
    color: red;
    font-weight: bold;
    font-size: 1.5rem;
  }

  form{
    input{
      background-color: black;
      padding: 5px;
      border: 2px solid red;
      border-radius: 10px;
      color: white;
      margin-right: 20px;
    }
    input::placeholder{
        color:white;
    }
    button{
      padding: 5px;
      border-radius: 10px;
      background-color: red;
      color: white;
      border: 2px solid red;
    }
  }
}


</style>
