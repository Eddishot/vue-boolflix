<template>
  <div id="app">
    <div class="input-group my-2  mx-auto" style="max-width:400px">
      <input   type="text" class="form-control" placeholder="Cerca cosa vuoi guardare..." aria-label="Recipient's username" aria-describedby="basic-addon2">
      <div class="input-group-append">
        <button class="btn btn-outline-primary" type="button">Cerca</button>
      </div>
    </div>
    <ul>
      <li v-for="movie in movies" :key=movie.id>
        {{movie.title}}
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
          searchFilter: "",
          // typeQuery: "",

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

        userSearch(){
          axios
        .get(this.apiUrl + "/search/movie/", {

          params:{
            api_key:this.apiKey,
            query:"strange",
            language:"it",
            // query: this.typeQuery,
          }
        })
        .then((resp) => {
          
          this.movies =resp.data.results;
        });
        }
      },
      // mounted(){
        
      // }
    
  
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
