<template>
  <div id="app">
    <div class="input-group my-2  mx-auto" style="max-width:400px">
      <input v-model="typeQuery" @keyup.enter="filteredUserSearch"   type="text" class="form-control" placeholder="Cerca cosa vuoi guardare..." aria-label="Recipient's username" aria-describedby="basic-addon2">
      <div class="input-group-append">
        <button @click="filterdUserSearch" class="btn btn-outline-primary" type="button">Cerca</button>
      </div>
    </div>
    <ul>
      <li v-for="movie in movies" :key=movie.id>
        {{movie.title}}, {{movie.vote_average}}, ({{movie.original_title}}), {{movie.original_language}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  components: {},
      data(){
        
        return{
          apiKey:"f2e0ba98e179316e4a7f99a330f592c6",
          apiUrl: "https://api.themoviedb.org/3",
          movies:[],
          series:[],
          // searchFilter: "",
          typeQuery: "",

          // urlEndType: {
          //   movie: "/search/movie",
          //   tv:"/search/tv"

          // },

          // apiData:{
          //   series:[],
          //   movie:[],
          // }
        }
        
      },
      methods:{
        // funzione principale
        userSearch(url, typeGenre){
           axios
                .get(this.apiUrl + url, {

                  params:{
                    api_key:this.apiKey,
                    query: this.typeQuery,
                    language:"it",

                    // query: this.typeQuery,
                  }
                })
                .then((resp) => {
                  
                  this[typeGenre] =resp.data.results;
                });
        },
          //  funzioni per la ricerca di film e serietv
        filterdUserSearch(){
          this.userSearch("/search/movie", "strange", "movies"); 

          this.userSearch("/search/movie", "strange", "series");
      },
        
      },
      mounted(){
        
      
      
      }
      
}
    
  

</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
// @import "~font-awesome/css/font-awesome.min.css";

// #app {
//   font-family: Avenir, Helvetica, Arial, sans-serif;
//   -webkit-font-smoothing: antialiased;
//   -moz-osx-font-smoothing: grayscale;
//   text-align: center;
//   color: #2c3e50;
//   margin-top: 60px;
// }
</style>
