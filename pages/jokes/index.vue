<template>
  <div>
    <SearchJokes v-on:search-text="searchJoke"/>
    <Joke v-for="joke in jokes" v-bind:key="joke.id" v-bind:id="joke.id" v-bind:joke="joke.joke"/>
  </div>
</template>

<script>
import axios from 'axios';
import Joke from '../../components/Joke';
import SearchJokes from '../../components/SearchJokes';
export default {
  components:{
    Joke,
    SearchJokes
  },
  data(){
    return{
      jokes:[]
    }
  },
  methods:{
    async searchJoke(text){
      const config= {
      headers:{
        Accept: "application/json"
      }
    };
    try {
      const res= await axios.get(`https://icanhazdadjoke.com/search?term=${text}`,config);
      this.jokes=res.data.results;
      // console.log(res.data);
    } catch (err) {
      console.log(err);
    }
    }
  },
  async created(){
    const config= {
      headers:{
        Accept: "application/json"
      }
    };
    try {
      const res= await axios.get("https://icanhazdadjoke.com/search",config);
      this.jokes=res.data.results;
      // console.log(res.data);
    } catch (err) {
      console.log(err);
    }
  },
  head(){
    return{
      title: "Dad jokes",
      meta:[
        {
          hid:'description',
          name:'description',
          content: 'best place for corny dad jokes'
        }
      ]
    }
  }
}
</script>
