<template>
    <div>
        <h1>Boolflix</h1>
        <div class="input-group m-2"  style="max-width:400px">
            <input type="text" class="form-control" placeholder="Recipient's username" aria-label="Recipient's username" aria-describedby="basic-addon2">
            <div class="input-group-append">
                <button class="btn btn-outline-primary" type="button">Button</button>
            </div>
        </div>
    </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'Nav',
  
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

<style>

</style>